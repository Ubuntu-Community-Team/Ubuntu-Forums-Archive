---
title: "Piping to LPR"
date: 2004-12-04
forum: Hardware &amp; Laptops
---

### Post by bob k on 2004-12-04
I have a Samsung ML-1740 which is a ML-1710 with faster print speed.

The problem I have is when I pipe the output of lets say a man page to lpr the page doesn't center and the page chops the top half of the line at the top of the page and does the same thing at the bottom of the page, except it is the bottom half, and loses the left most character. I have  tried groff and troff with out any improvement. I'm sure it is a command that I can't remember, and the damn thing is most probably an option in man.

---

### Post by WW on 2004-12-05
> ... the damn thing is most probably an option in man.Indeed it is, **-t**.  For example,```
 $ man -t inkscape | lpr
```prints a nice copy of the inkscape man page.

---

### Post by bob k on 2004-12-05
[QUOTE=WW]Indeed it is, **-t**.  For example,```
 $ man -t inkscape | lpr
```prints a nice copy of the inkscape man page.[/QUOTE]

Some times you can't see the Forrest because of the trees.
That worked great. I had to get over the out of paper thing. With the red light blinking at you for no apparent reason, so the first thing you do is unplug every thing, anyway I got it working. I guess I'll put a little script  in my local bashrc to fix that.

Thanks and happy Holidays

Bob

---

### Post by tacubuntuforums on 2004-12-20
[QUOTE=bob k]I have a Samsung ML-1740 which is a ML-1710 with faster print speed.

The problem I have is when I pipe the output of lets say a man page to lpr the page doesn't center and the page chops the top half of the line at the top of the page and does the same thing at the bottom of the page, except it is the bottom half, and loses the left most character. I have  tried groff and troff with out any improvement. I'm sure it is a command that I can't remember, and the damn thing is most probably an option in man.[/QUOTE]
 maybe this also helps:

**man** [-t] *page* | pr | lpr

---

