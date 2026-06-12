---
title: "Printer Margins for refcards (HP PSC)"
date: 2006-02-12
forum: Hardware &amp; Laptops
---

### Post by Gianni Exile on 2006-02-12
Hi,

I have an HP PSC-1210, and the margins are messed up.

I tried alignmargins.pl, it had no effect.

Currently I resort to printing dvi and pdf files to postscript and manually edit the postscript to adjust the margins.  Needless to say this is a waste of time.  

PROBLEM

Pick a refcard, e.g. /usr/share/doc/gdb/refcard.ps.gz
Type: lp /usr/share/doc/gdb/refcard.ps.gz
Result: The orientation is wrong, only the second two out of three columns show up, the rest is cut off.

Type: kprinter /usr/share/doc/gdb/refcard.ps.gz, press "Print"
Result: The orientation is correct, but the margins cut off 1in from the top.

Type: kprinter /usr/share/doc/gdb/refcard.ps.gz, set margins, press "Print"
Result: Same as last time.

Type: gzip -d -c /usr/share/doc/gdb/refcard.ps.gz | mpage -1 -bletter -m36 > out.ps ; kprinter out.ps
Result: Orientation wrong, 2 or 3 inch margin on one side, cutoff on other.

I have tried about a dozen combinations, none of them work.

I even tried using the binary-only non-free acroread, and it shrinks refcards so they print all on the page, but the alignment is off so they can't be glued together and folded.

My own program I wrote to fix them works for only some postscript files, not most.

Each new task seems to require more hand-coded postscript and at least three tries.  How do people print refcards, or cd covers, or mailing labels, or anything requiring any precision?  

Thanks for any advice.

---

