# Template LaTeX per tesi di laurea @ UniTS

[![Build LaTeX document](https://github.com/peiva-git/thesis_template/actions/workflows/compile-pdf.yml/badge.svg)](https://github.com/peiva-git/thesis_template/actions/workflows/compile-pdf.yml)
![License](https://img.shields.io/github/license/peiva-git/thesis_template)

![Template ita](https://img.shields.io/github/downloads/peiva-git/thesis_template/ita%2Fv1.0/total)
![Template eng](https://img.shields.io/github/downloads/peiva-git/thesis_template/eng%2Fv1.0/total)


Questo repository contiene un _template_ base, scritto in LaTeX,
da utilizzare per la propria tesi di Laurea Triennale o Magistrale
presso l'[Università degli Studi di Trieste](https://www.units.it/).

Nella sezione _Releases_ sono disponibili due versioni, una da utilizzare per la tesi in italiano,
e una per la tesi in inglese.

## Indice

1. [Requisiti](#requisiti)
2. [Ambiente di sviluppo](#ambiente-di-sviluppo)
3. [Istruzioni per la compilazione](#istruzioni-per-la-compilazione)
4. [Confronto fra versioni](#confronto-fra-versioni)
5. [Ringraziamenti](#ringraziamenti)

## Requisiti

In ambiente Linux e utilizzando `aptitude` come _package manager_,
eseguire il comando seguente per installare i pacchetti necessari alla compilazione:
```shell
apt install texmaker texlive-babel-italian texlive-hyphen-italian texlive-subfigmat texlive-appendix texlive-bibtex-extra biber
```

## Ambiente di sviluppo

Oltre a [Overleaf](https://www.overleaf.com/), è disponibile anche un [plugin](https://plugins.jetbrains.com/plugin/9473-texify-idea)
che permette l'utilizzo dell'IDE Jetbrains IntelliJ con LaTeX.
Questo repository è stato realizzato utilizzando quest'ultima opzione.

## Istruzioni per la compilazione

**L'approccio consigliato** per la compilazione è quello di utilizzare il comando `latexmk`.
Questo è facilmente installabile tramite:
```shell
apt install latexmk
```

Eseguendo il seguente comando, il sistema di _build_ di `latexmk` si occuperà di gestire tutta la procedura
di compilazione, facendo uso del [file di configurazione](.latexmkrc),
senza bisogno di specificare alcuna opzione aggiuntiva!
```shell
cd thesis_template/
latexmk
```

Il file compilato finale `thesis.pdf` e tutti i file prodotti saranno disponibili nella cartella `out/`.

Inoltre, eseguendo il comando `latexmk -c`, verranno rimossi tutti i file rigenerabili, ovvero tutti tranne
`thesis.pdf` e `thesis.bbl`. Maggiori informazioni sono disponibili [qui](https://mg.readthedocs.io/latexmk.html).

In alternativa, per compilare la tesi in formato `pdf`, è possibile eseguire i seguenti comandi:
```shell
cd thesis_template/
pdflatex thesis.tex
biber thesis.bcf
pdflatex thesis.tex
pdflatex thesis.tex
```

## Confronto fra versioni

Può essere utile confrontare le varie versioni della tesi utilizzando lo strumento di versionamento `git`.
A tal proposito, è sufficiente installare il comando `git-latexdiff`, tramite `apt install latexdiff`.
Ad esempio, per confrontare il `HEAD` con la versione precedente di due commit, eseguire:
```shell
cd thesis_template/
git-latexdiff --main thesis.tex --latexmk --build-dir out/ -o out/thesis_diff.pdf HEAD~2
```
Più informazione e alcuni esempi sono disponibili [qui](https://ctan.org/tex-archive/support/git-latexdiff).

## Ringraziamenti

Per la struttura della tesi è stato utilizzato il _template_ reso disponibile dal prof. Sergio Carrato
[qui](https://www2.units.it/carrato/didatt/info_laureandi/LaTeX/template/).
Si ringrazia l'autore, Stefano Bianchi, per averlo reso disponibile e si ringrazia il prof. Alberto Carini
per aver aggiunto le istruzioni sull'utilizzo.

SI ringrazia Tommaso Fonda per aver reso disponibile il _template_ in inglese.
