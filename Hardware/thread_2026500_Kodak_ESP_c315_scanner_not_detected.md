---
title: "Kodak ESP c315 scanner not detected?"
date: 2012-07-15
forum: Hardware
---

### Post by a26776500 on 2012-07-15
Hello:

I've got a all in one printer called Kodak ESP c315.

But I'll got a issues is the scanner not work so how do I getting it work?

When I run simple scan,I've got this result
" scanner not detected"

How do I get it work? Please help me,thank you so much!

---

### Post by paulnewall on 2012-07-16
There is a how to here
[https://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/](https://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/)

---

### Post by edcompsci on 2012-07-31
What about for AMD64? I think I've tried everything.

1. Downloaded the tar and compiled it. Fine, the printer works great. No scanning.
2. Downloaded SANE from the GIT repository, installed SANE from that. still no scanning.
3. Recompiled the driver again, then re-added the printer with the new ppd file.

still no scanning.


I'm using Lucid Lynx.

I am going to try this in the new LTS in a VM and see what happens

---

### Post by paulnewall on 2012-08-01
If the printer is printing, don't spend time reinstalling it. You need to regard the printer and the scanner as entirely separate devices that happen to be in the same box.

Are you using a usb or network/wifi connection?

There are a lot of things that have to be right for the scanner to work. The HowTo suggests a procedure to follow - what results do you get at each stage?

---

### Post by paulnewall on 2012-09-09
The kodak AiO scanning driver is now in the official release of sane-backends 1.0.23. I guess that means it might find it's way into your distro's repository in the next 6 months or so. See:
[http://www.sane-project.org/](http://www.sane-project.org/)

I also put a copy of that release here
[http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/](http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/)

---

