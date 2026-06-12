---
title: "Dell Inspiron 6000 weird shutdown noise"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by varchar255 on 2007-05-08
Hi all,

I have a standard Dell Inspiron 6000 laptop with no unusual hardware. I am dual-booting XP and Feisty. Normally, the machine can be forcibly shut down by holding down the power button for several seconds. When I do that, the hard disk (?) makes a distinct sharp whine as it powers down which is very disturbing. If I shut down the laptop from Windows, the fans turn off and the machine quietly stops, but if I shut down from Feisty, the machine makes the same horrible noise. It seems like something is going wrong with the Feisty shutdown if I'm getting the same "forced termination" noise...is this happening to anyone else, or does anyone know anything about it?

Thanks!

---

### Post by ninocass on 2007-05-11
i get this noise myself i think its the hardrive and the fan stopping so sharply where as windos steps them down a bit slower maybe?

---

### Post by Rescue9 on 2007-05-12
Yea... I get that same noise too. However, I've also noted that if I hard shutdown during bios post I get the same sound.

Dell I8500

---

### Post by zcal on 2007-05-14
Glad I'm not the only one getting this problem.  Check out [my post]("http://ubuntuforums.org/showthread.php?t=441785") about this issue.  I still have no idea what to do about it though, but it worries me...a lot.  Did you guys experience this problem with an previous versions, or is it just Feisty for you too?

IBM Thinkpad R40, by the way.

*edit*
Okay, check out this thread.  [http://ubuntuforums.org/showthread.php?t=404977&highlight=shutdown+noise](http://ubuntuforums.org/showthread.php?t=404977&highlight=shutdown+noise)

It seems to be a kernel bug, which has been confirmed and is high priority according to [this Launchpad report]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810").  Seems like the best solution at the moment is to add the script described in the Launchpad report (also in the Ubuntu forums thread) or either boot with Edgy's kernel.  I'm on a friend's computer for the moment, so I'll try those solutions out later.  Buena suerte.

---

### Post by psycosmyth on 2007-05-16
thanks ZCAL! 
This has been haunting me. I have an Inspiron 1200. Same problem.
It happens with any Distro using 2.6.20 and up to 21.

---

### Post by zcal on 2007-05-29
The kernel update to 2.6.20.16 fixed this problem for me.  :D

---

### Post by zcal on 2007-06-12
Newest kernel update started this problem again.  I guess it's back to the patch...  Anybody else?

---

