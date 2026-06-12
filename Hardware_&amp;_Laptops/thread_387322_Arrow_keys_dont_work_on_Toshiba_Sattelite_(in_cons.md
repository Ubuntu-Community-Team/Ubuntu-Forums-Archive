---
title: "Arrow keys dont work on Toshiba Sattelite (in console)"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by jay019 on 2007-03-18
Hi All,

I have Ubuntu running on my toshi laptop, all is good except for an odd problem.

Whenever I try an use vi in a console the arrow keys dont work. Instead of moving the cursor like they should they instead type the letters "ABCD" depending on which one i press. They work fine in any X based text editor, but sometimes 'vi filename' is much quicker than opening a graphical text editor for a simple job. 

Any ideas what needs to be fixed???

Cheers.

Jay

---

### Post by lloyd_b on 2007-03-18
There seems to be a problem with terminal emulation and the "vim-tiny" that's installed by default ("vi" is just a symlink to whichever version of "vim" is installed).

A couple of possible fixes:
1.  Set your TERM to "ansi" (i.e. "export TERM=ansi"). 
2.  Install the "vim" or "vim-full" package (they don't appear to have this problem).

Lloyd B.

---

