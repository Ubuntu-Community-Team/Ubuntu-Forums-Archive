---
title: "/dev/thinkpad does not exist (or has disappeared)"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by steffen on 2005-04-11
On my Warty Thinkpad T40, on screen display, powermanagement, etc. worked perfectly.

However, after upgrading, I noticed that on-screen display had disappeared, and even when I re-start tpb -d nothing shows up when I click the buttons.

When I try to run tpctl to configure, I get message > tpctl: Neither /dev/thinkpad/thinkpad nor /dev/thinkpad exists. Exiting.  Anyone know why my Thinkpad module has disappeared? I have all the necessary packages installed, I believe.

Thanks to anyone who might have an idea...

---

### Post by alastair on 2005-04-11
I have a thinkpad and haven't used this. But I suspect that it's a "udev" issue i.e. you need to either add a rule, or a static "create this device" option, to "udev".

I assume this would be mentioned in any docs "tpctl" (etc.) install e.g. chech under /usr/share/doc. Failing that, there is probably a web page/mailing list for this application with the answer.

---

### Post by steffen on 2005-04-13
Hmmm...I just assumed that it was already configured, since my laptop was detected as a Thinkpad on first Hoary install. But I guess it's not that easy. I'll have to look into it, and probably configure some stuff manually, I guess...

Thanks for your reply!

---

### Post by uglysmurf on 2005-04-26
I've got the same problem...any updates?

---

### Post by alastair on 2005-04-27
A simple google search for : /dev/thinkpad udev linux

found many pages that might help e.g.

[http://lists.debian.org/debian-laptop/2005/02/msg00051.html](http://lists.debian.org/debian-laptop/2005/02/msg00051.html)

---

### Post by hagan on 2005-05-19
Look here for solution on not working OSD

[http://www.ubuntuforums.org/showthread.php?t=24685](http://www.ubuntuforums.org/showthread.php?t=24685)

---

### Post by emendelson on 2005-05-19
You don't need /dev/thinkpad for these functions; what you need is the line "thinkpad" in /etc/modules and the correct, non-Hoary version of tpb.

Just follow the instructions here and all the ThinkPad buttons will work properly with full on-screen display support.

[http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html#tpbosd](http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html#tpbosd)

---

