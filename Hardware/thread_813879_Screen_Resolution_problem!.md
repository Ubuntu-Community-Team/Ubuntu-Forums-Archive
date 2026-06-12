---
title: "Screen Resolution problem!"
date: 2008-05-31
forum: Hardware
---

### Post by cenoura on 2008-05-31
Hi,
I'm trying to connect my laptop to an 22" external monitor. The problem is that Screen Resolution doesn't display the correct resolution for the monitor (which is 1680x1050).
On the other distros all I needed to do was run "sudo dpgk-reconfigure xserver-xorg" and select the right res.

Thanks in advance
By the way, my laptop is an Acer Aspire 1652WLMi w/ ATI X300 and the monitor is a Fujtsu Scaleoview L22W-3

---

### Post by paulphillips on 2008-05-31
I presume you tried that and it didn't work?

---

### Post by cenoura on 2008-05-31
Yes, now in hardy sudo dpkg-reconfigure xserver-xorg has keyboard options and a more few options... they took away lots of options..And the xorg.conf is much shorter than the other versions:( I've also tried to edit xorg.conf, by adding resolutions but no success

any hints?

---

### Post by ajgreeny on 2008-05-31
Are there any restricted drivers for the graphics card in the machine that you can enable?  If so that may help.

---

### Post by cenoura on 2008-05-31
Yes, running FGLRX very good... Compiz is also working w/out problems
My Screen Resolution displays resolutions up to 1280x800, all I need is the 1680x1050
:confused:

EDIT: I've tried a fresh install, the screen resolutions with and without the restricted drivers were the same

---

### Post by cenoura on 2008-06-03
:confused:any hint?

---

