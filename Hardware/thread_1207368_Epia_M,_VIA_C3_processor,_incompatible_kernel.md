---
title: "Epia M, VIA C3 processor, incompatible kernel"
date: 2009-07-08
forum: Hardware
---

### Post by crazyaxe on 2009-07-08
Hello everybody.
I'm trying to install Ubuntu 9.04 on a VIA C3 Epia M PC.
512Mb RAM
533MHz fanless

but works only the liveCD boot.
If I try to install I obtain only a black screen.
Is there any installation without graphic?
Please help.

However I obtain the same result with Mandriva, but not with Slackware. I don't know why Slackware 12 works.

---

### Post by Kuno81 on 2009-07-10
Hi crazyaxe,

the Live-CD boot menu offers some option. One is something like "video safe mode", i guess...
Keep on trying, i installed the 9.04 on my Epia M10000 few days ago. Everything works out-of-the-box. Except the hardware rendering doesn't work perfectly, but it works.

Good luck!

---

### Post by lavinog on 2009-07-27
I have the 800Mhz (fan) version. My system crashes within minutes of booting.
Apparently this has something to do with a module called longhaul being compiled into the kernel.
This page:[http://bugzilla.kernel.org/show_bug.cgi?id=10062](http://bugzilla.kernel.org/show_bug.cgi?id=10062) seems to mention that longhaul is very buggy with the older via boards, and it isn't included in the kernel because of instability. For some reason it is enabled by default in ubuntu: CONFIG_X86_LONGHAUL=Y
I will try and compile a custom kernel with this dissabled later this week to see if this fixes the issue.

---

### Post by lavinog on 2009-07-30
adding notsc to the kernel options at boot seemed to fix my epia issues. You may want to give it a try.

---

