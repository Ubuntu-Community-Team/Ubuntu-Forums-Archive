---
title: "two pointer devices"
date: 2010-02-04
forum: Hardware
---

### Post by itchy8me on 2010-02-04
hi,

I'm trying to find out how i can get two pointers enabled on my system. I have two mice and two displays.. me and my wife often use my main desktop, she watches stuff on the net and i look up information, play games or watch other stuff. It would be great if i could get two pointers to work independent of each other.

now i have stumbled upon this:
[http://wearables.unisa.edu.au/mpx/](http://wearables.unisa.edu.au/mpx/)

which is supposed to enable support for 2 pointers. however the page is redundant. the new blog hints at merging with xorg and indeed this is what i find on wikipedia:

> 
MPX was created by Peter Hutterer in 2005-2008, as part of his PhD in the Wearable Computer Lab under the supervision of Prof. Bruce H. Thomas at the University of South Australia.
MPX was merged into the current development version of X.Org on 26 May 2008[1].
Xinput2 (XI2) which is the second official stable API release of the XInput X Window Extension, containing MPX was merged into the current development version of X.Org on 3 June 2009[2]



now i am wondering how i am supposed to get it installed/configured in xorg. can anyone help?

thanks.

---

### Post by LowSky on 2010-02-04
if I remember you could always run two sessions and therefor two sets of pointers that way.

---

### Post by itchy8me on 2010-02-04
> **LowSky said:**
> if I remember you could always run two sessions and therefor two sets of pointers that way.

2 sessions as in 2 xserver sessions?

---

### Post by LowSky on 2010-02-04
Yes, Sorry I dont have a link but its completley possible.

---

### Post by Rhubarb on 2010-02-24
If you try out Ubuntu 10.04 alpha (lucid lynx), MPX works quite well.
There's a quick howto here: [http://alec.mooo.com/mpx.php](http://alec.mooo.com/mpx.php)

I just tested it out with lucid alpha 2 (from today's snapshot), it works nicely.

There is a few bugs in it though, such as only 1 mouse cursor will work at a time within that application for some applications.

Eg, you can't drag more than 1 window on the screen once, or open the menu up with 1 mouse, and use the other mouse to select the menu option.

But it should fine for 2 separate applications.
It's possible to have more than 1 keyboard and mouse with MPX.

---

