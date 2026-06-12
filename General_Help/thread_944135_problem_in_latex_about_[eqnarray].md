---
title: "problem in latex about [eqnarray]"
date: 2008-10-11
forum: General Help
---

### Post by subjugater on 2008-10-11
Hi, folks,

This is actually a pure latex question and nothing to do with ubuntu, though I'm using latex on my ubuntu system. 

I am trying to generate an equation array which consists of about 10 lines.

In fact, this array starts at the bottom of one page and is expected to be continued on the next page. But latex treats this array as a whole. Since the array can not fit in the rest of the current page, Latex postpone the whole array to the next page by leaving the rest of current page just blank.

I am wondering if latex can split the array into two part to avoid that ugly blank at the bottom of the current page. What should I do?

Any comments? Thanks a lot!

---

### Post by Stefan_K on 2008-10-12
Hi subjugater,

at first: don't use eqnarray, it's obsolete and produces inconsistent spacing. Use the align environment of amsmath instead. For a short explanation with screenshot and sourcecode have a look here: _[eqnarray vs. align]("http://texblog.net/latex-archive/maths/eqnarray-align-environment/")_.

amsmath provides commands concerning page breaks inside multiline formulas: \allowdisplaybreaks and \displaybreak. You will find them documented by the _[amsmath user's guide]("ftp://ftp.ams.org/pub/tex/doc/amsmath/amsldoc.pdf")_.

If you still have questions regarding this subject feel free to ask.

Stefan

---

