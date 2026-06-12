---
title: "How do I run TeX Live after installing full version"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by maporojo on 2009-02-04
I have been using LaTeX on a Mac OS X at work but now I want to be writing .tex files from home on a machine where Ubuntu 8.10 has been installed.

I need to be able to make research equations from home for those days that I do not make it to the office and .tex files are the only acceptable way of writing those statements.

I installed Tex Live using: sudo apt-get install texlive-full

(The installation took some time but everything went flawlessly, I believe.)

I was expecting to see a short-cut for launching it added in one of the menus (e.g. Accessories, Office, etc.) but I did not see one.

Is there a way to launch it from the command prompt?

Is it graphic based like LaTeX is on Mac OS X once I launch it?

---

### Post by zika on 2009-02-04
You've installed TeX engine. You can either run it with any editor for preparing .tex files and compiling them on command-line in Terminal or You could install one of several TeX-oriented editors to make it more or less graphical. I'm using Kile and I'm very satisfied but there is also LyX that is even more WYSIWYG. it is too much WYSIWYG for me. either way You can use Synaptic to choose ... there is a poll going on about which is the best editor for LaTeX ... check it out ... it might help. I've found it: [http://ubuntuforums.org/showthread.php?p=6665327](http://ubuntuforums.org/showthread.php?p=6665327)

---

### Post by maporojo on 2009-02-04
Thanks for the reply. I'm very new to Linux and TeX so pardon my amateur level questions.

Does Kile need the TeX Live engine I installed in order to work or, may I remove TeX Live, install Kile, and still be able to generate .pdf files from Kile?

There is a gedit-LaTeX plug-in available at [http://www.michaels-website.de/2009/01/gedit-latex-plugin-02-rc1-available/](http://www.michaels-website.de/2009/01/gedit-latex-plugin-02-rc1-available/)

Since TeX Live is a LaTeX distribution for Ubuntu, does it mean that I can use gedit to generate the .pdf files once I install the plug-in?

Below is a file called test.tex for which I'd like to generate a .pdf file having already installed TeX Live.

(LaTeX on the Mac OS X at work readily generated the test.pdf file.)

\documentclass[12pt]{article}

\usepackage{fullpage}

\addtolength{\oddsidemargin}{-.5in}
\addtolength{\evensidemargin}{-.5in}
\addtolength{\textwidth}{.75in}
\addtolength{\topmargin}{-.5in}
\addtolength{\textheight}{.75in}

\usepackage{graphicx}
\usepackage{epstopdf}

\begin{document}

\textbf{ABC XYZ}

The governing equations are:
\[
\theta_i = \omega_i + \frac{K}{N} \sum_{j=1}^N \sin (\theta_j - \theta_i) \mbox{ where } i = 1, \ldots, N.
\]

%\begin{figure}[h]
%\begin{center}
%\includegraphics[width=\hsize]{fig1.eps}
%\end{center}
%\caption{\small Constant , $k = 1$.}
%\label{fig-label}
%\end{figure}

\end{document}

---

### Post by zika on 2009-02-04
> **maporojo said:**
> Thanks for the reply. I'm very new to Linux and TeX so pardon my amateur level questions. Does Kile need the TeX Live engine I installed in order to work or, may I remove TeX Live, install Kile, and still be able to generate .pdf files from Kile?

no, You are on the right path. just add (install) Kile, it will use texlive that You've already acquired. 
(my grandmother (I'm 51) always tould me that no one was born with knowledge ... it has to be a(c)quired ... ;) do not apologize, please ... we all are just returning the favors we were given in this or some other forum already.)

---

### Post by maporojo on 2009-02-04
Thanks a lot! I am able to use Kile for a single .tex file. The larger article I have has different files for each chapter and a .bib file for the bibliography. I hope Kile will handle the bibliographies properly. I had to compile (four times ) the .tex file that added (via "\include") the other .tex files and a .bib file in LaTeX on a Mac in order to get the bibliographies and page numbers done correctly. I'm not sure how to do this with Kile but I will try.

---

### Post by astrobob.tk on 2010-07-20
> **maporojo said:**
> I have been using LaTeX on a Mac OS X at work but now I want to be writing .tex files from home on a machine where Ubuntu 8.10 has been installed.

I need to be able to make research equations from home for those days that I do not make it to the office and .tex files are the only acceptable way of writing those statements.

I installed Tex Live using: sudo apt-get install texlive-full

(The installation took some time but everything went flawlessly, I believe.)

I was expecting to see a short-cut for launching it added in one of the menus (e.g. Accessories, Office, etc.) but I did not see one.

Is there a way to launch it from the command prompt?

Is it graphic based like LaTeX is on Mac OS X once I launch it?


I was in a similar confusion though I don't know LaTeX nor have I ever tried working with it until recently. I am writing my lab reports (& learning a bit of LaTeX) using LyX. LyX is WYSIWYM -What You See Is What You Mean- contrary to WYSISYG -What You See Is What  You Get- LaTeX-based word processor. I think its powerful & simple to use. Though I am new to such software but I already started learning some Tex codes.
I am not sure how Kile is as I never tried it but I recommend you try LyX. I assume Kile requires a KDE environment, something I don't like or use. LyX works on both KDE (haven't tried it) & GNOME. Check out the official page at [www.lyx.org](www.lyx.org)

Oh & by the way. It not only works on Linux, but its Cross Platform :D

good luck ;)

---

### Post by arun ganesh on 2011-03-17
Actually i too had the same problem..
first basic step is to go the Teminal in your Ubuntu Os
type these commands

sudo apt-get install latex                 (for tex file will insatll all the dependency packages) 
sudo apt-get install latex-beamer    (for lpresentaions/slides)
sudo apt-get install lyx                    (for your tex editor like notepad,emac etc)
  i say best editor is gedit ... no other editor can replace it..

just type your tex file in gedit and save it as file.tex
in terminal or command line compile as follows:
latex file.tex
or
pdflatex file.tex
 and also tex-live are bianries like extra packages..it's not a gui...
u can also check your version simply typing latex or pdflatex...

hope u'll enjoy

---

### Post by pandanator on 2012-01-10
This thread was very helpful - I just installed TeX Live myself, for use in school. My GUI bias made it so that I kept looking for the texlive app. :P Learning things is hard!

---

