---
title: "producing landscape PDFs with latex"
date: 2008-09-22
forum: General Help
---

### Post by coverup1128 on 2008-09-22
I have a weird problem with PDF documents formatted as landscape. I use latex to produce the PDF, but it does not show as landscape on the screen - instead, I see a square shaped page, and the content of the slide stretches beyond the right-hand edge of the page. Naturally, the content that does not fit that square page is lost.

Interestingly, the document formats just fine using latex and ghostscript in Mandriva Linux. This tells me that there is nothing wrong with the document, and something is broken in Ubuntu. Any ideas/help how to fix this annyoance?

---

### Post by tacutu on 2008-09-22
are you using evince to view the resulting dvi / pdf? Evince has some strange bugs when it comes to margins (and I think also paper layout)

---

### Post by mannheim on 2008-09-22
The following works for me using Ubuntu 8.04 and texlive from the repositories. My test file looks like:
```
\documentclass[landscape]{article}

\pdfpagewidth 11in
\pdfpageheight 8.5in

\begin{document}
Hello World.
\end{document}

```

If I do "pdflatex test.tex" and then view the resulting pdf file in evince or in acrobat reader, it displays correctly. Note that the "landscape" option just tells the tex engine the dimensions of the region on which to lay out the text. (tex itself doesn't have much idea of physical page size.) The commands \pdfpagewidth and \pdfpageheight are needed also, otherwise you get landscape typesetting on a potrait page.

Perhaps some latex package provides a less verbose way to do this.

---

### Post by TeXtonyx on 2008-09-22
[http://launchpadlibrarian.net/10628852/CologneCompact.pdf](http://launchpadlibrarian.net/10628852/CologneCompact.pdf)

That is a landscape document that view fine with Evince 2.22.2
I used to build webpages and sometimes the code would work in Netscape but 
not in IE, or vice versa. And it did not mean that the code was correct and
that one browser was broken in some respect. Usually, the browser which 
displayed the webpage did so because its enforcement was to lax, so I had
to fix the code before it would work in both. 
I mean that the conclusion regarding Mandriva and Ubuntu remains uncertain.
Those kind of inferences are difficult to draw even for experts. 

Most likely it means your document is amiss, but it possible that you have 
installed slightly incompatible version packages if you downloaded and 
installed some on your own but relied on synaptic for others for Ubuntu, but
used all the defaults for populating Mandriva with applications. There are 
no doubt possibilities that are quite unpredictable.

---

### Post by coverup1128 on 2008-09-22
Thanks for the replies, everyone.

I tried the suggested "Hello world" and it displays fine in Adobe Reader 8 if printed with dvips -t landscape, and then converted into PDF using ps2pdf. I am aware of evince problems, and avoid using it.

I would still maintain that the document is fine, and the problem caused by texlive; it was downloaded using synaptics.

My document uses the seminar style, and the proposed landscape+pdftextwidth solution did not work with it. However, the document renders fine on all versions of Mandriva from 6.1 to the latest 2008, on Ubuntu 6.06 LTS, and on Windows computers using MikTeX without those modifiations. I know from a colleague that it works fine on a Red Hat PC. My feeling is that the bug sits somewhere in the Hardy's distribution of texlive. Is it possible to downgrade to the original tetex?

Edit: I narrowed down the problem to dvips behaving differently in Ubuntu and other TeX distributions I have. Ubuntu ships with dvips 5.96 and Mandriva 2008 eg with 5.95, but I guess it's a bunch of other files that reside in dvips subdir that are different as well. So, the downgrade may be the way to go.

---

### Post by tacutu on 2008-09-23
why downgrade? Instead, maybe you could try upgrading to the new Telive 2008, see if that works for you.

---

### Post by coverup1128 on 2008-09-23
> **tacutu said:**
> why downgrade? Instead, maybe you could try upgrading to the new Telive 2008, see if that works for you.
I have tetex on other systems, downgrading will make it easier for me to work with the same document on other systems. Besides, I am not so sure that TexLive 2008 is reliable enough:

[http://www.redhat.com/archives/rhl-devel-list/2008-September/msg00131.html](http://www.redhat.com/archives/rhl-devel-list/2008-September/msg00131.html)

---

### Post by TeXtonyx on 2008-09-23
[http://www.radicaleye.com/dvips.html](http://www.radicaleye.com/dvips.html)

That is the webpage with has the email address of the develper of Dvips. 
He might be able to suggest an easier fix for your problem than a
downgrade. Usually a newer package fixes more problems than it creates.
The major distros have different standards and cycles for upgrading their 
repositories. I used to subscribe to the LyX mailing list and TexLive was
almost always behind in adding newer versions of packages and they didn't
care about Windows releases. OpenSuse 11 has put emphasis on Kde4 which 
will please some people and not others. That is both the strength and
the weakness of Linux, diversity. I like the cream of elegant solution(s).

---

### Post by coverup1128 on 2008-09-25
Bump... Is there way to install the original tetex?

> **coverup1128 said:**
> I have tetex on other systems, downgrading will make it easier for me to work with the same document on other systems. Besides, I am not so sure that TexLive 2008 is reliable enough:

[http://www.redhat.com/archives/rhl-devel-list/2008-September/msg00131.html](http://www.redhat.com/archives/rhl-devel-list/2008-September/msg00131.html)

---

### Post by Stefan_K on 2008-10-12
teTeX is obsolete since years, I wouldn't recommend to install it.
Regarding the landscape problem you could try geometry with the landscape option:
```
\usepackage[landscape]{geometry}
```

Stefan

---

### Post by coverup1128 on 2008-10-17
Stefan, thank you for your suggestions. None of the workarounds proposed by you on the launchpad work for me. I consistently get a PDF with page size 8.26x8.50in and the text truncated on the right. I use seminar in my document.

The problem only occurs in Ubuntu Hardy. I have used the same template for years to produce slides. It still works fine under Mandriva 2008.0.

---

### Post by Stefan_K on 2008-10-17
Hi,

if you post a [minmal working example]("http://minimalbeispiel.de/mini-en.html") I would know your packages and settings and could help to fix it.

Stefan

---

### Post by coverup1128 on 2008-10-18
Thanks for the willingness to help. 

I tried to create a simple example, and found that plain seminar or beamer examples work fine. The problem arises when I include third-party styles which however work fine with tetex. I used these styles called Utopia bundle for many years but their website is no longer maintained.

---

