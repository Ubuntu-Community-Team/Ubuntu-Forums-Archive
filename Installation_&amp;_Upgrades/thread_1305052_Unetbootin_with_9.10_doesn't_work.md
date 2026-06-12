---
title: "Unetbootin with 9.10 doesn't work??"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by snowman4839 on 2009-10-29
I love unetbootin and I used to use it all the time but recently it has been acting up. I have a 1GB flash drive and I'm trying to put 9.10 on it. I got the prerelease to work on my laptop with windows XP but when I tried to install, it said "errno 5: read write error" so I decided to redo it with unetbootin.(I couldn't do it with my laptop again because the "partial install" deleted the GRUB loader so I couldn't boot into XP) On my desktop, I tried on vista multiple times and it didn't work, I tried with a virtual machine of XP, and now I'm trying on ubuntu 9.04 but all of these stop at the 9th item "filesystem.sqashfs". I've been waiting for almost half an hour (on ubuntu 9.04) and it is still on the 9th item. I've tried with normal privlages and sudo privlages but still nothing... What the heck is wrong??

---

### Post by snowman4839 on 2009-10-29
anyone?!?!?

---

### Post by mikewhatever on 2009-10-29
Jaunty has it's own program to make a bootable usb, usb-creator.

---

### Post by snowman4839 on 2009-10-29
> **mikewhatever said:**
> Jaunty has it's own program to make a bootable usb, usb-creator.
I'm trying that right now. It didn't work but it seems to be the drive itself. It worked fine with another second flash drive

---

### Post by Anxiety35 on 2009-10-29
> **snowman4839 said:**
> I love unetbootin and I used to use it all the time but recently it has been acting up. I have a 1GB flash drive and I'm trying to put 9.10 on it. I got the prerelease to work on my laptop with windows XP but when I tried to install, it said "errno 5: read write error" so I decided to redo it with unetbootin.(I couldn't do it with my laptop again because the "partial install" deleted the GRUB loader so I couldn't boot into XP) On my desktop, I tried on vista multiple times and it didn't work, I tried with a virtual machine of XP, and now I'm trying on ubuntu 9.04 but all of these stop at the 9th item "filesystem.sqashfs". I've been waiting for almost half an hour (on ubuntu 9.04) and it is still on the 9th item. I've tried with normal privlages and sudo privlages but still nothing... What the heck is wrong??

I tried twice with unetbootin and had no luck. It appeared to have worked correctly, but when booting from my flash drive, the Ubuntu loading screen takes several minutes before saying it can't find the kernel files and dumping me in a command prompt.

I'm trying the Jaunty program now. I haven't had much luck with it in the past though.

---

### Post by DJKnut on 2009-10-30
I just loaded my laptop (that wouldn't recognize or boot the CD..) by using unetbootin and the same CD for the ISO loaded onto a 4 GB stick, and everything worked GREAT!!! I like simple answers...  Dave

---

