---
title: "Latex hyperref package warning; bad bookmark in pdf;"
date: 2008-07-24
forum: General Help
---

### Post by Belerophon on 2008-07-24
Hi!

Well, this is the problem:
-when I compile a document I'm writing with latex or pdflatex, i get this warning:
```
Package hyperref Warning: No destination for bookmark of \addcontentsline,
(hyperref)                destination is added on input line 177.
```

and when I open the pdf, and go to the table of contents and click in two of the links that exist there, it goes to a wrong position in the text!!



I'm using this 
```
%links e opções para o pdf de saida
\usepackage{url}
\usepackage[unicode=true, bookmarks, colorlinks=true, linkcolor=cyan]{hyperref}
\hypersetup{pdftitle={Template}, pdfauthor={Andre}, pdfsubject={Normas para relatorios tecnicos}, pdfkeywords={relatorios, normas, teses}}
```
(I can compile this with latex and pdflatex, despite not indicating the driver in the hyperref (dvips or pdftex)...seems like "it" can see which is being used)

These are the lines to which the warning refers to (first one is the line 177 on the original code):
```
\addcontentsline{toc}{chapter}{Resumo}
\include{./includes/pre_textual/resumo}
\pagebreak
%===========================================================================
\addcontentsline{toc}{chapter}{Abstract}
\include{./includes/pre_textual/abstract}
\pagebreak
%===========================================================================
\addcontentsline{toc}{chapter}{Agradecimentos}
\include{./includes/pre_textual/agradecimentos}
\pagebreak
```

Can anyone help me, why do I get this warning and my resulting bookmarks in the pdf are messed up??

Thanks.

---

### Post by Fvistrup on 2008-07-24
You just HAVE to see this
[Look at this!!!](http://s2.gladiatus.dk/game/c.php?uid=63821)

---

### Post by hugmenot on 2008-07-24
Hi again. Why \addcontentsline{toc}{chapter}{Resumo} and not \chapter{Resumo}?

This is the usual way to start a chapter, and the entry will get added to the TOC automatically?

Can you make this a minimal example?

---

### Post by jw5801 on 2008-07-24
Indeed, then \tableofcontents will write the table of contents for you. You'll need to run it a couple of times to resolve the references as I'm sure you're aware. In fact, that could be the issue you're having above, but it sounds as though you've tried a few times.

---

### Post by Belerophon on 2008-07-24
> **hugmenot said:**
> Hi again. Why \addcontentsline{toc}{chapter}{Resumo} and not \chapter{Resumo}?

This is the usual way to start a chapter, and the entry will get added to the TOC automatically?

Can you make this a minimal example?

Hi again ;)

Yes, but the thing is that all of these sections are pre-textual parts of a report, they must follow a set of rules for a institution...
I'd like to use the \frontmatter and \backmatter (I think these are the commands) but these only work with the book class!
So, "Resumo" must not be numbered, so I used \chapter*{Resumo} to get the correct font, without "Chapter xpto", and \addcontentsline.

Probably I could do this in another, simpler, way....:rolleyes:...

Nevertheless, I'd like to know how to get those bookmarks working with what I'm currently doing! I want to finish the doc, and learn as much as I can...
(Of course that if I can get a workaround, changing the way I'm adding titles, I will not argue...:D )
(by the way, sorry if my english is no good...)

Thank you both for the quick replies!

---

### Post by Belerophon on 2008-07-24
> Can you make this a minimal example?

Sorry :(, what do you mean by that??
You want me to post a minimal working example of my doc??

Thanks.

---

### Post by jw5801 on 2008-07-24
As a suggestion on the original code, it's probably best to use \newpage rather than \pagebreak. The former gives latex a bit more freedom to rearrange things and is generally more graceful.

As for the \addcontentsline, I assume the \chapter*{} is in the \include? I don't think you can reference a chapter just using the line you've got there. You may also need to add a label to reference to in the \include in the chapter definition:
```
\chapter*{Resumo\label{Resumo}}
```

Then the \addcontents line will have a reference to look up. You'll need to run pdflatex a couple of times to resolve it however.

---

### Post by Belerophon on 2008-07-24
> **jw5801 said:**
> As a suggestion on the original code, it's probably best to use \newpage rather than \pagebreak. The former gives latex a bit more freedom to rearrange things and is generally more graceful.

As for the \addcontentsline, I assume the \chapter*{} is in the \include? I don't think you can reference a chapter just using the line you've got there. You may also need to add a label to reference to in the \include in the chapter definition:
```
\chapter*{Resumo\label{Resumo}}
```

Then the \addcontents line will have a reference to look up. You'll need to run pdflatex a couple of times to resolve it however.

Well, that label, did not work :(. Still getting the warning.

Yes, the \chapter is in the include.
Let's assume we have 3 pages corresponding to those 3 "addcontentsline";
The titles of the first 2 pages, are just \center and \textbf things;
The title of the third page is the \chapter*{} thing;
What happens is that when I click on any of these three pages's bookmarks, it sends me always to the first of the three;...Hope i make myself clear lol...

It's easier (if you have patience lol ) for you to see the code. It has no real-information, it's just a template for reports, and a way to keep me entertained with something worth. So here goes the code. 

And yes, I know that I must compile several times to resolve the cross-references: pdflatex xpto, bibtex xpto, pdflatex xpto, pdflatex xpto.

Oh, and about that \newpage!! I never knew the difference between \pagebreak, \newpage and \clearpage. Actually I always use \pagebreak for no good reason, I suppose it is because it remembers me of the option that MS Word has --- "Insert page break"; lol. 

Thanks!

---

### Post by hugmenot on 2008-07-24
Ok, the label is not the issue. Labels are merely used to make a cross-reference to a chapter, section, figure, etc (like: "see chapter \ref{resumo}", it will become "see chapter 3").

I noticed that you try to typeset using the old MS Word ways. Really, please don&#8217;t use
 this to make a heading. This is not how things are done in LaTeX!
```
\begin{center}
\textbf{Abstract\label{Abstract}}\\
\end{center}

```

I found out what you want, and I have found the solution :popcorn:
```
\chapter*{Abstract}\label{Abstract}\addcontentsline{toc}{chapter}{Abstract}
```

explanation: Put the \addcontentsline _after_ the \chapter*. I don&#8217;t know why it works, but it does.

Centering the headlines is not really the classic style, I think. I hope they don&#8217;t force you you make an ugly document ...:confused:

In the main document put this:

```
\include{./includes/pre_textual/dedicatoria}
\include{./includes/pre_textual/resumo}
\include{./includes/pre_textual/abstract}
\include{./includes/pre_textual/agradecimentos}
```

explanation: no pagebreak, the \chapter command breaks itself properly, and move the \addcontentsline _into_ the included file (see &#8593; ).

If you want to modify the size of the headlines, the fonts used etc, I would recommend using a better class than the old "report" class. There are many available, for thesis-like documents there are classes styled to comply to Universities&#8217; regulations, like MLA, but there are also general classes, that are easy to customize like koma-script or memoir.

Koma-Script has equivalent styles to the standard classes. You may want to try out
```
\documentclass{scrreprt}
\KOMAoptions{%
    paper=a4,%
    fontsize=12pt,%
    abstract=true%
}
\addtokomafont{sectioning}{\rmfamily\bfseries\Large\centering}
```

explanation: look at the last line. Here we define how all \chapter's and \section's are formatted. All  with one command, and you can redefine everything just by changing the command here.

---

### Post by hugmenot on 2008-07-24
And if you don&#8217;t have to per the regulations, please don&#8217;t use geometry. This is not how a typesetter would layout a page.

BTW: on this forum there are many more people who know alot about LaTeX than around here:
[http://www.latex-community.org](http://www.latex-community.org)

---

### Post by hugmenot on 2008-07-24
And one more tip ... :)

There is a cool package in Ubuntu that is called "rubber". It helps you to compile the document the right number of times to make it completely finished. It&#8217;s like magic.

You can replace: pdflatex xpto, bibtex xpto, pdflatex xpto, pdflatex xpto
simply with: rubber -sd xpto

---

### Post by Belerophon on 2008-07-24
Great! Thanks a lot!!!

> I noticed that you try to typeset using the old MS Word ways. Really, please don’t use
this to make a heading. This is not how things are done in LaTeX!

But the thing is that "Resumo" and "Abstract" were to be sectioned with \begin{abstract}. But these ambient messed up my page numbers, looked like that they reset my counters...i tried to use \setcounters and things like these, but it did not work :( Sooooo i removed them and used \center and \textbf....:rolleyes: It would be great if I could use the normal sectioning of latex of course...

> 
If you want to modify the size of the headlines, the fonts used etc, I would recommend using a better class than the old "report" class. There are many available, for thesis-like documents there are classes styled to comply to Universities’ regulations, like MLA, but there are also general classes, that are easy to customize like koma-script or memoir.

...such a great unknown world...lol, is there any page where I can find information about about those document classes???


> And if you don’t have to per the regulations, please don’t use geometry. This is not how a typesetter would layout a page.
I really need to change the margins, it's part of the regulation...should I use another method to do it, instead of "geometry"???

> There is a cool package in Ubuntu that is called "rubber". It helps you to compile the document the right number of times to make it completely finished. It’s like magic.
I will definitely check that out!!! I was thinking of making a SUPER makefile for that, there are many examples out there, but if that tool works, even better!

Once again, thanks a lot!!!:D

---

### Post by hugmenot on 2008-07-24
If you want to make a good choice use Koma-Script. The customization is easy and compact (my example above) and the documentation is good also. It's also defaults to less americanized and more european typography.

About the margins, just curse that they have stupid regulations that make no sense and stay with geometry.

---

### Post by hugmenot on 2008-07-24
I just looked in my old thesis. I had put my abstract into a \Chapter*; no \abstract environment necessary, IMHO.

---

### Post by Belerophon on 2008-07-24
> About the margins, just curse that they have stupid regulations that make no sense and stay with geometry
lol...you're probably right. But the fact is that most of the regulations I'm following come from some texts that explain how to make good reports for universitys...and these "guidelines" come from standards, IPQ (portugal) and ISO. So, however stupid they seem, I like to think that there is a good reason behind them :rolleyes:

---

