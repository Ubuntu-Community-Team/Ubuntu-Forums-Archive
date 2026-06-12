---
title: "kile compiling"
date: 2008-08-25
forum: General Help
---

### Post by weemstra on 2008-08-25
Hello,

I have .tex document produced in windows and I am trying to compile it in kile with PDFLaTeX, but for some reason it does not work. The file is : 

\begin{center}

\vspace{6cm}

{\Huge\bf\sf Statuten \\ der \\ Utrechtse Geologen Vereniging }

\vspace{13cm}

{\Large\bf\sf\itshape zoals vastgesteld op 11 september 2001, \\
bij N. van Buitenen,\\
notaris te Utrecht.}

\vspace{\fill}

\end{center}
\newpage




Error messages from kile:


[PDFLaTeX] statuten2001test.tex => statuten2001test.pdf (pdflatex)
[PDFLaTeX] finished with exit status 1
./statuten2001test.tex:1:Missing \begin{document}. \begin{center}
./statuten2001test.tex:1:Overfull \hbox (20.0pt too wide) in paragraph
./statuten2001test.tex:5:Undefined control sequence. {\Huge
./statuten2001test.tex:5:Undefined control sequence. {\Huge\bf
./statuten2001test.tex:5:Undefined control sequence. {\Huge\bf\sf
./statuten2001test.tex:9:Undefined control sequence. {\Large
./statuten2001test.tex:9:Undefined control sequence. {\Large\bf
./statuten2001test.tex:9:Undefined control sequence. {\Large\bf\sf
./statuten2001test.tex:9:Overfull \hbox (20.44432pt too wide) in paragraph
./statuten2001test.tex:9:Overfull \hbox (20.69984pt too wide) in paragraph
./statuten2001test.tex:9:Overfull \hbox (28.87756pt too wide) in paragraph
./statuten2001test.tex:9:Overfull \hbox (10.22217pt too wide) in paragraph
./statuten2001test.tex:9:Overfull \hbox (10.22217pt too wide) in paragraph
./statuten2001test.tex:9:Overfull \hbox (33.47754pt too wide) in paragraph
./statuten2001test.tex:9:Overfull \hbox (12.90543pt too wide) in paragraph
./statuten2001test.tex:9:Overfull \hbox (23.51099pt too wide) in paragraph
./statuten2001test.tex:10:Overfull \hbox (10.73326pt too wide) in paragraph
./statuten2001test.tex:10:Overfull \hbox (10.49994pt too wide) in paragraph
./statuten2001test.tex:10:Overfull \hbox (15.33324pt too wide) in paragraph
./statuten2001test.tex:10:Overfull \hbox (26.97203pt too wide) in paragraph
./statuten2001test.tex:10:Overfull \hbox (18.911pt too wide) in paragraph
./statuten2001test.tex:11:Overfull \hbox (30.5387pt too wide) in paragraph
./statuten2001test.tex:11:Overfull \hbox (7.92215pt too wide) in paragraph
./statuten2001test.tex:11:Overfull \hbox (34.6497pt too wide) in paragraph
./statuten2001test.tex:16:The font size command \normalsize is not defined:there is probably something wrong with the class file. \newpage
statuten2001test.tex:0:Emergency stop.
[PDFLaTeX] 9 errors, 0 warnings, 17 badboxes




Does anyone has an idea, what the problem might be??
thanks in advance.

---

### Post by Nepherte on 2008-08-25
> **weemstra said:**
> ./statuten2001test.tex:1:Missing \begin{document}. \begin{center}
./statuten2001test.tex:5:Undefined control sequence. {\Huge
./statuten2001test.tex:5:Undefined control sequence. {\Huge\bf
./statuten2001test.tex:5:Undefined control sequence. {\Huge\bf\sf
./statuten2001test.tex:9:Undefined control sequence. {\Large
./statuten2001test.tex:9:Undefined control sequence. {\Large\bf
./statuten2001test.tex:16:The font size command \normalsize is not defined:there is probably something wrong with the class file. \newpage
These are your errors. It seems like it doesn't know the command \normalsize so you either haven't imported a required library or the command just doesn't exist. For the 'undefined control sequences' the syntax is probably wrong. I don't know the exact syntax for it, but to me those starting '{' are not in its place.

I can recommend the following to latex resources:
[http://tobi.oetiker.ch/lshort/lshort.pdf](http://tobi.oetiker.ch/lshort/lshort.pdf) - The not so short introduction to latex
[http://en.wikibooks.org/wiki/LaTeX](http://en.wikibooks.org/wiki/LaTeX) - The latex wikibook.

---

### Post by tacutu on 2008-08-25
if this is your entire file, it won't ever compile. Latex files need a preamble:

\documentclass{article}
\begin{document}

look at the log file: is says 
./statuten2001test.tex:1:Missing \begin{document}. \begin{center}

Just as Nepherte said, you should read "The not so short introduction to latex" to get you started.

---

