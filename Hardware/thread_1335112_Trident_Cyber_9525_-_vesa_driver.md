---
title: "Trident Cyber 9525 - vesa driver"
date: 2009-11-23
forum: Hardware
---

### Post by Andy Carlos on 2009-11-23
Hello

I use Linux on an old laptop and am having problems with the configuration of "xorg.conf"
My video card is a Trident Cyber 9525 and when I use the Trident driver, I have a problem with scrambled lines at the bottom of the screen.
Usually, in other linux distributions I fix this using the vesa driver.
In xorg.conf I change the line
Driver "trident"
By
Driver "vesa"
But on ubuntu 8.04, when I do this fix, when you start X, the screen is scrambled and blinking.
What should I do?

Thank you.

---

### Post by Andy Carlos on 2009-11-24
SOLVED: I just change xorg.conf with this line:

 **   DefaultDepth    16**
in Section "Screen".

Thanks.

---

### Post by doctor casey on 2012-04-20
How do you get to a terminal and then to xorg.conf to make changes?

---

### Post by oldos2er on 2012-04-20
Closed. Please start a new thread for your question.

---

