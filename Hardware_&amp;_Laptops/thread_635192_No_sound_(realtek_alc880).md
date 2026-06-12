---
title: "No sound (realtek alc880)"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by white_devil on 2007-12-08
Hello, i have just installed ubuntu 7.10 with compiz fusion and i have no sound at all.

I have followed a few sites, like this:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://ubuntuforums.org/showthread.php?t=133325](http://ubuntuforums.org/showthread.php?t=133325)
[http://www.larsen-b.com/Article/87.html](http://www.larsen-b.com/Article/87.html)

but nothing seems to work.

When i type alsamixer on terminal, the mixer shows up and it recognize my soundcard and doesnt show up any error at boot or anything, but i just dont know what else can i do.

Any help please? :(

Thank you

---

### Post by white_devil on 2007-12-16
Any reply, please?

Thx in advanced

---

### Post by inphektion on 2007-12-16
this worked for me:
sudo aptitude install linux-backports-modules-generic
and then a reboot.

---

