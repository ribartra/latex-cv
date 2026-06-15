# latex-cv

Currículum (CV) escrito en LaTeX. El fuente es [`cv.tex`](cv.tex) y el resultado compilado es [`cv.pdf`](cv.pdf).

## Requisitos

El documento usa `pdflatex` y los paquetes `geometry`, `titlesec`, `enumitem`, `hyperref`, `fontawesome`, `tabularx` y `array`.

## Crear el PDF en Ubuntu

### 1. Instalar LaTeX

```bash
sudo apt update
sudo apt install texlive-latex-base texlive-latex-extra texlive-fonts-extra
```

> El paquete `fontawesome` (iconos) viene en `texlive-fonts-extra`, y `titlesec`/`enumitem`/`tabularx` en `texlive-latex-extra`. Si quieres la instalación completa sin preocuparte por paquetes faltantes, usa `sudo apt install texlive-full` (ocupa más espacio).

### 2. Compilar

Desde la carpeta del repositorio:

```bash
pdflatex cv.tex
```

Esto genera `cv.pdf`. El propio `hyperref` puede requerir una segunda pasada para resolver referencias; si ves avisos de referencias, ejecútalo dos veces:

```bash
pdflatex cv.tex && pdflatex cv.tex
```

### 3. Ver el PDF

```bash
xdg-open cv.pdf
```

## Recompilar automáticamente al editar (opcional)

Con `latexmk` puedes recompilar cada vez que guardes cambios en `cv.tex`:

```bash
sudo apt install latexmk
latexmk -pdf -pvc cv.tex
```

## Limpiar archivos intermedios

La compilación crea archivos auxiliares (`cv.aux`, `cv.log`, `cv.out`) que están en `.gitignore` y no se versionan. Para borrarlos:

```bash
latexmk -c          # con latexmk
# o manualmente:
rm -f cv.aux cv.log cv.out
```
