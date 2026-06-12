---
title: "Random black screen on resume from suspend"
date: 2010-10-25
forum: Hardware
---

### Post by Vermind on 2010-10-25
Hi,
I have an Asus UL30VT laptop with dual graphics cards. I am using the intel card, while both cards are visible from lspci. The system is an Ubuntu 10.10 install, though the issue also presented itself on 10.04.
I also turn the nvidia graphics card off on system startup using the acpi_call module [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html) .

When I suspend the laptop and resume it, about 50% of the time it comes back to a black screen. Keyboard and mouse work, but it just appears that the screen will not turn on. Pressing display on/off buttons or brightness buttons does nothing, and re-suspending and resuming does nothing. Ctrl-alt-F1 and Ctrl-Alt-Del reboots the machine normally.

The longer the laptop stays suspended, the more likely it is that I get a black screen on resume.

Any ideas?
Next thing I am going to try is to make acpi_call turn the nvidia off on resume as well, if the nvidia card is the problem somehow...

---

### Post by preacher258 on 2011-02-14
Maybe the same issue as this thread? I'm having a similar problem, btw.

---

### Post by preacher258 on 2011-02-14
[http://guide.ubuntuforums.org/showthread.php?p=10458275#post10458275](http://guide.ubuntuforums.org/showthread.php?p=10458275#post10458275)

oops, forgot to paste it ;)

---

