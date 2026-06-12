---
title: "Dual Boot (yes I read the help)"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by Skemcin on 2009-10-05
Hi,

I am in the process of pretty much changing my entire house to Ubuntu - huge fan.  I've gotten an old laptop (formerly Windows XP) formatted and now fully functional with Ubuntu.  I have two desktops left.  I am currently working on Desktop Number 1 and my issue is that it recently decided to not boot Windows at all - it must know what's coming.  At work I successfully installed Ubuntu as a dual boot since I am able to boot into Windows first (and follow instructions).  But that is now the case at home now.

So, my questions is, how can I install Ubuntu onDesktop 1 without loosing anything on the hard drive?  And will I be able to access the files on the hard drive or will they not be able to see each other?

I've been able to boot Desktop 1 from Ubuntu CD - which is an official CD from Ubuntu, version 8.04 I think.  I can operate just fine from the CD but I can't access the root harddrive or the other two I have in that PC.  Am I SOL?

Please help. And thank you in advance for your assistance.

---

### Post by apb2390 on 2009-10-05
You can use gparted (in System>Administration>Partiton Editor) on the live CD to shrink the Windows partition and make a new one for Ubuntu. Make sure you defrag the hard drive in Windows first. And yes, they will be visible to each other as different drives.

---

### Post by Skemcin on 2009-10-06
> **apb2390 said:**
> You can use gparted (in System>Administration>Partiton Editor) on the live CD to shrink the Windows partition and make a new one for Ubuntu. Make sure you defrag the hard drive in Windows first. And yes, they will be visible to each other as different drives.
Thanks for the reply.  My problem is that I cannot defrag Windows from windows since I've not been able to get it to boot up in windows.  I'm gonna try DOS next, but was wondering if there were other options.

---

### Post by tuahaa on 2009-10-06
If you're asking if you can access the other partition, well then probably (in my case anyway). I had Linux Mint and Ubuntu installed, and I shrunk my Linux Mint to 14gb, and so in ubuntu it showed as a 14gb device, where I could access all my files from Ubuntu

---

