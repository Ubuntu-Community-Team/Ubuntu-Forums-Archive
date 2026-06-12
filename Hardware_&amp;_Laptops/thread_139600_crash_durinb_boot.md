---
title: "crash durinb boot"
date: 2006-03-04
forum: Hardware &amp; Laptops
---

### Post by damu on 2006-03-04
Hi
I updated the kernel to have dual core supported as suggested in forums.

Since, if I boot with this new kernel , it crashs at "configuring network devices".
I have to hard reboot.

Asus av8 deluxe
x2 3800+
wifi : wl-130g (working fine on the original kernel)
Ubuntu for i386 (I tried the AMD64 version...too many problems for a newbiee..)

any suggestions?

---

### Post by NiceGuy on 2006-03-06
Are you sure it is crashing? When I have my laptop disconnected from my network it pauses for AGES at that point when booting. I think it has somthing to do with DHCP but I'm not sure. I normally press 'Ctrl + C' to skip that step. There has to be a better way to do it and stop it probing the network (or at least taking so long to do it) - it is a laptop after all!

---

### Post by NiceGuy on 2006-03-06
I've found a better way than pressing Ctrl + C!

[http://www.ubuntuforums.org/showthread.php?p=798819#post798819]("http://www.ubuntuforums.org/showthread.php?p=798819#post798819")

---

### Post by damu on 2006-03-07
When I boot from the default ubuntu breezy kernel, the step "configuring network devices" takes a while (and I could probably try to  spped it up), but it works...all in one, my ubuntu experience is sooo great, that I try to find some ways to run flash MX and Director MX under linux , to definitely forget about Win!!"...

But when I try to boot on the smp kernel, it get stuck at the step "configuring network devices", exit the graphical boot environnement, and switch to a black screen with the lines of booting  process on screen. 
Caps Lock still works, so it is not completely crashed... but it keeps stuck at that step and I can't boot

---

### Post by damu on 2006-03-10
I sent a bug report on that one, but I am still stuck with either booting without smp , or this bug.

For administrative work, working with one core is fine, but for video and sound editing, and multitask, it is not an option

it defeats the object of having an AMD X2...

Any help very much appreciated 

Thanks

---

### Post by damu on 2006-03-13
I guess I will wait for Dapper to have smp enabled...tried the control C during the boot process when it gets stuck @ "configuring network devices" with no results"

---

