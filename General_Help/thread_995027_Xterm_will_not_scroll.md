---
title: "Xterm will not scroll"
date: 2008-11-27
forum: General Help
---

### Post by JanusDuo on 2008-11-27
I have edited my rc.local to run startx, then to run an xterm.  I then plan to run a program that has a graphical X window element and a terminal log output type element.  Its working great, except that the text fills the xterm then keeps going but the xterm doesn't scroll to keep up with it.

I've ran a bunch of searches but I can't figure out how to fix this.  I tried all the xterm command line switches to enable the different types of scrolling (jump scrolling, scroll on terminal output to xterm) but it just does the same thing.  That am I doing wrong?

---

### Post by Severun on 2008-11-27
have you tried launching xterm w/ the -sb flag to add the scroll bar?

---

### Post by JanusDuo on 2008-11-27
I don't want to be able to scroll it manually, (and yes I can get a side scrollbar that is nonfunctional that way) I want it to keep scrolled to the bottom even with new input, just like a non-graphical terminal would.

I'm using the +si switch.

From the man page-"This option indicates that output to a window should cause it to scroll to the bottom. "

It's not working.  I start my X screens with either xinit, startx, or just X, then I call xterm and specify, "geometry 640x480, scroll on input, font color grey, background color black, font 12X10" etc.  No scroll, once I run out of real estate (one "ls -al") and it just keeps outputting below the screen where I cant see it as the screen doesn't scroll down to follow.

Thing is the xterm that xinit loads automatically DOES scroll, it's just scrunched in a corner of the screen and white background/black text with small font which I want to change and thus must start my own term window.

---

