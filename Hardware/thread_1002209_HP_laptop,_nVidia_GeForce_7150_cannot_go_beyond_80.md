---
title: "HP laptop, nVidia GeForce 7150 cannot go beyond 800x600 resolution"
date: 2008-12-04
forum: Hardware
---

### Post by samturri on 2008-12-04
Hello all,

Just installed 8.10.  It's my first (working) Linux install.

Everything seems to be going well with one exception: I cannot go beyond 800x600 res.  I have a HP Pavilion dv2840se, which I'm fairly certain has a nVidia GeForce 7150 of some sort in it.  I've tried getting both open source and proprietary drivers to work, with no luck.  I've read that the 7150 in particular is problematic (apparently not supported by the official nVidia drivers?), but perhaps my newness to Linux is the real problem.

It seems like it's time to stop Googling and just ask the people that know...how do I get my display running in native resolution?

Thanks!

---

### Post by Private_Ops on 2008-12-04
That's odd. The included "Restricted Drivers" should work.

I've got a Compaq (cheap HP bascially) with the Nvidia 7150. I'm using the included 177 version drivers that are included with Ubuntu (well, in my case it's crunchbang linux (based off of ubuntu)).

You have tried enabling the drivers under "Restricted Drivers" have you not?

---

### Post by eskararriba on 2008-12-04
samturri, had the same problem just two days ago (HP, same nvidia card, same resolution problem) - and resolved it very easily by looking for "nvidia 177" in the add/remove tool. just install it and reboot. 
the solution is not mine, though... check this thread: [http://ubuntuforums.org/showthread.php?t=1000839](http://ubuntuforums.org/showthread.php?t=1000839) 

hope it ll work for you as well, cheers

---

### Post by Issakar on 2009-10-21
Hi All, 

New to the forum, not quite as new to Ubuntu.

I just wanted to drop my 2 C worth. i have an HP dv6604nr that of course experiences the same issues with display and all. I was going to do the nvidia 177 package but it wouldnt let me due to incompatible hardware? weird. so i did the 173 instead, and now it works.

yay coffee!

---

