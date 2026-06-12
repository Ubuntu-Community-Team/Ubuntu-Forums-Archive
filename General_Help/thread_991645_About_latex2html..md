---
title: "About latex2html."
date: 2008-11-24
forum: General Help
---

### Post by NathanPrabhu on 2008-11-24
Is it possible to convert a tex file to html, when the tex file contains some phrase code translations. For example if my sample.tex file looks like this....

sample.tex

.......
.....
\expandafter\def\csname Label\endcsname{\translater{}}
\expandafter\def\csname EmpID\endcsname{\translater{ABC0562243}}
.....
...
\expandafter\def\csname FirstPhrase\endcsname{__P99-HERD-C22.12321350__}
.....
...
\expandafter\def\csname P99-HERD-C22.12321350\endcsname{\translater{å¦‚æžœå‘¼å¸ä¸è§„åˆ™æˆ–åœæ*¢,ç»™äºˆäººå·¥å‘¼å¸ã€‚}}
......
....


Here P99-HERD-C22.12321350 is the phrase code and the (å¦‚æžœå‘¼å¸.....) are the corresponding value(chinese symbol) for that phrase code.


Thanks in advance.

---

### Post by TeXtonyx on 2008-11-24
[http://www.cse.ohio-state.edu/~gurari/TeX4ht/](http://www.cse.ohio-state.edu/~gurari/TeX4ht/)

I think this is preferred to latex2html. Mathematical equations
are the hardest to convert faithfully. Sometimes code can be
inserted as a .jpeg or I think .eps now. So if something doesn't
look right in the html conversion, one can convert/insert an image. 
I used to do this with LyX a few years ago but I am not current.

---

