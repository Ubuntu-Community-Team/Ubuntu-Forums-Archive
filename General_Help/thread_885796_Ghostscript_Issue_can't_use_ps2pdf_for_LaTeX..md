---
title: "Ghostscript Issue: can't use ps2pdf for LaTeX."
date: 2008-08-10
forum: General Help
---

### Post by chenjin824 on 2008-08-10
Hi all,

Just switch to Ubuntu. When i tried to compile my .tex file to generate a 
pdf file. I failed at the very last step---ps2pdf. I was using .tex->.dvi->ps->pdf route to do it. When i test the intermediate result of this route, everything is all right but the very last step.
When i type in this command in the terminal:
$: ps2pdf filename.tex

It complains:
Error: /invalidfont in /findfont
Operand stack:
   Fh   138   --nostringval--   45   1   --nostringval--   45   4   --nostringval--   45   1   --nostringval--   45   1   --nostringval--   45   45   45   45   45   45   45   45   45   45   32   --nostringval--   45   6   --nostringval--   45   1   --nostringval--   45   4   --nostringval--   45   1   --nostringval--   45   1   --nostringval--   45   46   --nostringval--   --nostringval--   20   74.7198   Courier
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1889   1   3   %oparray_pop   1888   1   3   %oparray_pop   1872   1   3   %oparray_pop   1755   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   1847   49   4   %oparray_pop
Dictionary stack:
   --dict:1148/1684(ro)(G)--   --dict:0/20(G)--   --dict:94/200(L)--   --dict:106/300(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 45786
GPL Ghostscript SVN PRE-RELEASE 8.61: Unrecoverable error, exit code 1

The ghostscript i am using is GPL Ghostscript 8.61 (2007-11-21)
The version of ps2pdf I am using is 8.60. 

Seems like I miss some font files, but which ones? Where should I put them and how should i configure them? 

Thanks a lot!

---

### Post by hugmenot on 2008-08-11
Check the log file of your latex source file. If your document ist foo.tex, then open foo.log and look for font warnings or errors.

You can also try and switch to pdflatex, this will produce PDF in one step.

---

### Post by chenjin824 on 2008-08-11
Thanks for your reply, I am afraid I have to stick on this route because
we need to use the eps figure file incorporated in our paper. 

My recent discovery is that when i installed ghostscript, I have to install
its fonts separately. But when i turn to the documentation on its website, 
it doesn't tell me how to install it. 

When i type in this in the ternimal---
$: gs -help

it shows some search paths when ghostscript searches for fonts---
Search path:
   . : %rom%lib/ : /usr/local/share/ghostscript/8.61/lib :
   /usr/local/share/ghostscript/8.61/Resource :
   /usr/local/share/ghostscript/fonts :
   /usr/local/share/fonts/default/ghostscript :
   /usr/local/share/fonts/default/Type1 :
   /usr/local/share/fonts/default/TrueType : /usr/lib/DPS/outline/base :
   /usr/openwin/lib/X11/fonts/Type1 : /usr/openwin/lib/X11/fonts/TrueType


The weird phenomenon is that even if i copy all the fonts files from the package ghostscript-fonts-std.6.0-tar.bz2 into one of the paths mentioned above, /usr/local/share/ghostscript/8.61/Resource in my case, it still reports the exactly same error. 

The documentation says there is an environment variable GS_FONTPATH we could use the add some fonts path into it. But it doesn't tell us how to set up the variable. Anybody has any idea how to do it?

I don't know how to proceed...

---

### Post by hugmenot on 2008-08-12
I don&#8217;t think that Ghostscript needs all those fonts itself. Normally you only need to have the fonts installed in your TeX&#8217;s TEXMF tree. But I might be wrong on that.
Did you check the Latex log file?

Finally, using EPS with pdflatex is not possible, but you can simply convert EPS to PDF with the epstopdf command. Afterwards you'll have both files in your folder (figure.eps and figure.pdf) and if you leave out the extension as in \includegraphics{figure} both latex and pdflatex will choose their preferred format.
The only real reason to not use pdflatex is if you want to use pstricks and similar things.

---

### Post by chenjin824 on 2008-08-13
Yes, I checked about the path you've mentioned and those fonts files are there!

Here is a log file when use ps2pdf at the .ps file. Sorry for its
length. But anybody could help me diagnose and give me some suggestion? When i was using latex on Fedora Core 8, everything seems fine.

This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6) (format=latex 2008.8.9)  12 AUG 2008 20:35
entering extended mode
 %&-line parsing enabled.
**sample_v2.1.tex
(./sample_v2.1.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, pinyin, loaded.
(./ieeeconf.cls

LaTeX Warning: You have requested document class `ieeeconf',
               but the document class provides `cssconf'.

Document Class: cssconf 2004/1/15 revision V1.6b by Pradeep Misra
\@IEEEtrantmpdimenA=\dimen102
\@IEEEtrantmpdimenB=\dimen103
\@IEEEtrantmpcountA=\count79
\@IEEEtrantmpcountB=\count80
\@IEEEtrantmptoksA=\toks14
LaTeX Font Info:    Try loading font information for OT1+ptm on input line 792.

(/usr/share/texmf-texlive/tex/latex/psnfss/ot1ptm.fd
File: ot1ptm.fd 2001/06/04 font definitions for OT1/ptm.
)
\@IEEEnormalsizefontbaselineskip=\skip41

-- This is a 10 point document.
\normalsizebaselineskip=\skip42
\normaljot=\skip43
LaTeX Font Info:    Font shape `OT1/ptm/bx/n' in size <5> not available
(Font)              Font shape `OT1/ptm/b/n' tried instead on input line 1111.
LaTeX Font Info:    Font shape `OT1/ptm/bx/it' in size <5> not available
(Font)              Font shape `OT1/ptm/b/it' tried instead on input line 1111.

LaTeX Font Info:    Font shape `OT1/ptm/bx/n' in size <7> not available
(Font)              Font shape `OT1/ptm/b/n' tried instead on input line 1111.
LaTeX Font Info:    Font shape `OT1/ptm/bx/it' in size <7> not available
(Font)              Font shape `OT1/ptm/b/it' tried instead on input line 1111.

LaTeX Font Info:    Font shape `OT1/ptm/bx/n' in size <8> not available
(Font)              Font shape `OT1/ptm/b/n' tried instead on input line 1111.
LaTeX Font Info:    Font shape `OT1/ptm/bx/it' in size <8> not available
(Font)              Font shape `OT1/ptm/b/it' tried instead on input line 1111.

LaTeX Font Info:    Font shape `OT1/ptm/bx/n' in size <9> not available
(Font)              Font shape `OT1/ptm/b/n' tried instead on input line 1111.
LaTeX Font Info:    Font shape `OT1/ptm/bx/it' in size <9> not available
(Font)              Font shape `OT1/ptm/b/it' tried instead on input line 1111.

LaTeX Font Info:    Font shape `OT1/ptm/bx/n' in size <10> not available
(Font)              Font shape `OT1/ptm/b/n' tried instead on input line 1111.
LaTeX Font Info:    Font shape `OT1/ptm/bx/it' in size <10> not available
(Font)              Font shape `OT1/ptm/b/it' tried instead on input line 1111.

LaTeX Font Info:    Font shape `OT1/ptm/bx/n' in size <11> not available
(Font)              Font shape `OT1/ptm/b/n' tried instead on input line 1111.
LaTeX Font Info:    Font shape `OT1/ptm/bx/it' in size <11> not available
(Font)              Font shape `OT1/ptm/b/it' tried instead on input line 1111.

LaTeX Font Info:    Font shape `OT1/ptm/bx/n' in size <12> not available
(Font)              Font shape `OT1/ptm/b/n' tried instead on input line 1111.
LaTeX Font Info:    Font shape `OT1/ptm/bx/it' in size <12> not available
(Font)              Font shape `OT1/ptm/b/it' tried instead on input line 1111.

LaTeX Font Info:    Font shape `OT1/ptm/bx/n' in size <16> not available
(Font)              Font shape `OT1/ptm/b/n' tried instead on input line 1111.
LaTeX Font Info:    Font shape `OT1/ptm/bx/it' in size <16> not available
(Font)              Font shape `OT1/ptm/b/it' tried instead on input line 1111.

LaTeX Font Info:    Font shape `OT1/ptm/bx/n' in size <20> not available
(Font)              Font shape `OT1/ptm/b/n' tried instead on input line 1111.
LaTeX Font Info:    Font shape `OT1/ptm/bx/it' in size <20> not available
(Font)              Font shape `OT1/ptm/b/it' tried instead on input line 1111.

LaTeX Font Info:    Font shape `OT1/ptm/bx/n' in size <24> not available
(Font)              Font shape `OT1/ptm/b/n' tried instead on input line 1111.
LaTeX Font Info:    Font shape `OT1/ptm/bx/it' in size <24> not available
(Font)              Font shape `OT1/ptm/b/it' tried instead on input line 1111.

\IEEEilabelindentA=\dimen104
\IEEEilabelindentB=\dimen105
\IEEEilabelindent=\dimen106
\IEEEelabelindent=\dimen107
\IEEEdlabelindent=\dimen108
\labelindent=\dimen109
\IEEEiednormlabelsep=\dimen110
\IEEEiedmathlabelsep=\dimen111
\IEEEiedtopsep=\skip44
\c@section=\count81
\c@subsection=\count82
\c@subsubsection=\count83
\c@paragraph=\count84
\c@IEEEsubequation=\count85
\abovecaptionskip=\skip45
\belowcaptionskip=\skip46
\c@figure=\count86
\c@table=\count87
\@IEEEeqnnumcols=\count88
\@IEEEeqncolcnt=\count89
\@IEEEtmpitemindent=\dimen112
\c@biography=\count90
\@IEEEtranrubishbin=\box26
)
** ATTENTION: Overriding command lockouts (line 10).
** ATTENTION: Overriding IEEE standard margins (line 13).
(/usr/share/texmf-texlive/tex/latex/graphics/epsfig.sty
Package: epsfig 1999/02/16 v1.7a (e)psfig emulation (SPQR)

(/usr/share/texmf-texlive/tex/latex/graphics/graphicx.sty
Package: graphicx 1999/02/16 v1.0f Enhanced LaTeX Graphics (DPC,SPQR)

(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty
Package: keyval 1999/03/16 v1.13 key=value parser (DPC)
\KV@toks@=\toks15
)
(/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty
Package: graphics 2006/02/20 v1.0o Standard LaTeX Graphics (DPC,SPQR)

(/usr/share/texmf-texlive/tex/latex/graphics/trig.sty
Package: trig 1999/03/16 v1.09 sin cos tan (DPC)
)
(/etc/texmf/tex/latex/config/graphics.cfg
File: graphics.cfg 2007/01/18 v1.5 graphics configuration of teTeX/TeXLive
)
Package graphics Info: Driver file: dvips.def on input line 90.

(/usr/share/texmf-texlive/tex/latex/graphics/dvips.def
File: dvips.def 1999/02/16 v3.0i Driver-dependant file (DPC,SPQR)
))
\Gin@req@height=\dimen113
\Gin@req@width=\dimen114
)
\epsfxsize=\dimen115
\epsfysize=\dimen116
)
(/usr/share/texmf-texlive/tex/latex/pslatex/pslatex.sty
Package: pslatex 1996/07/24 v1.2 pslatex emulation (DPC)
LaTeX Font Info:    Redeclaring symbol font `operators' on input line 65.
LaTeX Font Info:    Overwriting symbol font `operators' in version `normal'
(Font)                  OT1/cmr/m/n --> OT1/ptmcm/m/n on input line 65.
LaTeX Font Info:    Overwriting symbol font `operators' in version `bold'
(Font)                  OT1/cmr/bx/n --> OT1/ptmcm/m/n on input line 65.
LaTeX Font Info:    Redeclaring symbol font `letters' on input line 66.
LaTeX Font Info:    Overwriting symbol font `letters' in version `normal'
(Font)                  OML/cmm/m/it --> OML/ptmcm/m/it on input line 66.
LaTeX Font Info:    Overwriting symbol font `letters' in version `bold'
(Font)                  OML/cmm/b/it --> OML/ptmcm/m/it on input line 66.
LaTeX Font Info:    Redeclaring symbol font `symbols' on input line 67.
LaTeX Font Info:    Overwriting symbol font `symbols' in version `normal'
(Font)                  OMS/cmsy/m/n --> OMS/pzccm/m/n on input line 67.
LaTeX Font Info:    Overwriting symbol font `symbols' in version `bold'
(Font)                  OMS/cmsy/b/n --> OMS/pzccm/m/n on input line 67.
LaTeX Font Info:    Redeclaring symbol font `largesymbols' on input line 68.
LaTeX Font Info:    Overwriting symbol font `largesymbols' in version `normal'
(Font)                  OMX/cmex/m/n --> OMX/psycm/m/n on input line 68.
LaTeX Font Info:    Overwriting symbol font `largesymbols' in version `bold'
(Font)                  OMX/cmex/m/n --> OMX/psycm/m/n on input line 68.
\symbold=\mathgroup4
\symitalic=\mathgroup5
LaTeX Font Info:    Redeclaring math alphabet \mathbf on input line 74.
LaTeX Font Info:    Overwriting math alphabet `\mathbf' in version `normal'
(Font)                  OT1/cmr/bx/n --> OT1/ptm/bx/n on input line 74.
LaTeX Font Info:    Overwriting math alphabet `\mathbf' in version `bold'
(Font)                  OT1/cmr/bx/n --> OT1/ptm/bx/n on input line 74.
LaTeX Font Info:    Redeclaring math alphabet \mathit on input line 75.
LaTeX Font Info:    Overwriting math alphabet `\mathit' in version `normal'
(Font)                  OT1/cmr/m/it --> OT1/ptm/m/it on input line 75.
LaTeX Font Info:    Overwriting math alphabet `\mathit' in version `bold'
(Font)                  OT1/cmr/bx/it --> OT1/ptm/m/it on input line 75.
) (./sample_v2.1.aux)
\openout1 = `sample_v2.1.aux'.

LaTeX Font Info:    Checking defaults for OML/cmm/m/it on input line 88.
LaTeX Font Info:    ... okay on input line 88.
LaTeX Font Info:    Checking defaults for T1/cmr/m/n on input line 88.
LaTeX Font Info:    ... okay on input line 88.
LaTeX Font Info:    Checking defaults for OT1/cmr/m/n on input line 88.
LaTeX Font Info:    ... okay on input line 88.
LaTeX Font Info:    Checking defaults for OMS/pzccm/m/n on input line 88.
LaTeX Font Info:    Try loading font information for OMS+pzccm on input line 88
.

(/usr/share/texmf-texlive/tex/latex/psnfss/omspzccm.fd
File: omspzccm.fd 2000/01/03 Fontinst v1.801 font definitions for OMS/pzccm.
)
LaTeX Font Info:    ... okay on input line 88.
LaTeX Font Info:    Checking defaults for OMX/cmex/m/n on input line 88.
LaTeX Font Info:    ... okay on input line 88.
LaTeX Font Info:    Checking defaults for U/cmr/m/n on input line 88.
LaTeX Font Info:    ... okay on input line 88.
LaTeX Font Info:    Try loading font information for OT1+ptmcm on input line 92
.

(/usr/share/texmf-texlive/tex/latex/psnfss/ot1ptmcm.fd
File: ot1ptmcm.fd 2000/01/03 Fontinst v1.801 font definitions for OT1/ptmcm.
)
LaTeX Font Info:    Try loading font information for OML+ptmcm on input line 92
.

(/usr/share/texmf-texlive/tex/latex/psnfss/omlptmcm.fd
File: omlptmcm.fd 2000/01/03 Fontinst v1.801 font definitions for OML/ptmcm.
)
LaTeX Font Info:    Try loading font information for OMX+psycm on input line 92
.

(/usr/share/texmf-texlive/tex/latex/psnfss/omxpsycm.fd
File: omxpsycm.fd 2000/01/03 Fontinst v1.801 font definitions for OMX/psycm.
)
LaTeX Font Info:    Font shape `OT1/ptm/bx/n' in size <6> not available
(Font)              Font shape `OT1/ptm/b/n' tried instead on input line 92.
 [1


]
LaTeX Font Info:    Font shape `OT1/ptm/bx/n' in size <7.4> not available
(Font)              Font shape `OT1/ptm/b/n' tried instead on input line 244.
File: snap1.eps Graphic file (type eps)
 <snap1.eps>
[2]
Underfull \vbox (badness 10000) has occurred while \output is active []

 [3]
File: subj3screenshot.eps Graphic file (type eps)

<subj3screenshot.eps> [4] [5] (./sample_v2.1.bbl)

** Conference Paper **
Before submitting the final camera ready copy, remember to:

 1. Manually equalize the lengths of two columns on the last page
 of your paper;

 2. Ensure that any PostScript and/or PDF output post-processing
 uses only Type 1 fonts and that every step in the generation
 process uses the US letter (8.5in X 11in) paper size.

[6] (./sample_v2.1.aux) ) 
Here is how much of TeX's memory you used:
 1388 strings out of 95081
 21061 string characters out of 1183121
 70987 words of memory out of 1500000
 4592 multiletter control sequences out of 10000+50000
 37989 words of font info for 87 fonts, out of 1200000 for 2000
 28 hyphenation exceptions out of 8191
 32i,8n,21p,1483b,283s stack positions out of 5000i,500n,6000p,200000b,5000s

Output written on sample_v2.1.dvi (6 pages, 43024 bytes).

---

### Post by hugmenot on 2008-08-15
can you try 

```
\usepackage[T1]{fontenc}
```

---

### Post by tacutu on 2008-08-15
> **chenjin824 said:**
> 
When i type in this command in the terminal:
$: ps2pdf filename.tex


Why are you trying to convert the .tex file?
shouldn't you do: 
```
ps2pdf filename.ps
```
instead?

---

### Post by chenjin824 on 2008-08-15
I tried your advice, but the errors are the same.

---

### Post by chenjin824 on 2008-08-15
Yes, should be like you said. I apologize for that typo.

---

### Post by kitturerahul on 2009-11-21
I am converting a ".djvu" file to ".pdf"
I gave following command 

"***djvups Burnside.djvu Burnside.ps***"

(here "Burnside.djvu" is my ".djvu" file, which I want to convert first in ".ps" form )
(".djvu" file had size 11.4 MB and after converting to ".ps" its size became 475MB)


Then I gave the following command :
  ***ps2pdf Burnside.ps Burnside.pdf***

Then it is showing followinf output

[I][B]Error: /rangecheck in --image--
Operand stack:
   --dict:8/8(L)--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1905   1   3   %oparray_pop   1904   1   3   %oparray_pop   1888   1   3   %oparray_pop   1771   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   1809   1   3   %oparray_pop
Dictionary stack:
   --dict:1154/1684(ro)(G)--   --dict:0/20(G)--   --dict:134/200(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 112119
GPL Ghostscript 8.62: Unrecoverable error, exit code 1
jtanti@bpstudent:~/Desktop$ [/B][/I]

How can we solve this problem?

---

