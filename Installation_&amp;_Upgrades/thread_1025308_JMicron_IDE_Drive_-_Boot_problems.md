---
title: "JMicron IDE Drive - Boot problems"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by mbateman on 2008-12-29
Hello everyone....

heres the issue.
cannot boot to installed ubuntu studio.
8.10 kernel 2.6.27
Jmicron controller BIOS 1.06.57

setup
ABIT AB9 Quad GT, Q6600, 3gb of RAM
this motherboar5d has the Jmicron controller for RAID etc.

I have 3 hard drives
1x ide 2x sata and a sata dvd drive.
I was able to install Ubuntu studio from CD onto the IDE drive(the other drives are full + Windows boot partition) but when I try to boot through GRUB I get the following

ALERT! dev/disk/by-UUID does not exist
dropping to a shell

its very unfortunate.

would anybody be able to help me?

---

### Post by caljohnsmith on 2008-12-30
How about trying this: when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the line add:
```
rootdelay=120
```
Press return to save the change, then press "b" to boot. Let me now if you still get the same error or if that works to boot Ubuntu.

---

### Post by mbateman on 2008-12-30
I have just completed this post from within ubuntu studio....

genius. thank you very much caljohnsmith!!!!!

so what does rootdelay=120 do?
is that milliseconds?

---

### Post by caljohnsmith on 2008-12-30
> **mbateman said:**
> I have just completed this post from within ubuntu studio....

genius. thank you very much caljohnsmith!!!!!

so what does rootdelay=120 do?
is that milliseconds?
This is just my own theory, but I think there is some sort of bug where the UUIDs that get created under /dev/disk/by-uuid/ directory are out of synch with the booting process, so that when the system goes to access them they haven't been created yet; adding the rootdelay to the kernel line causes the system to wait long enough while the pseudo files in /dev/disk/by-uuid are created. And I have no idea if the 120 is in actual milliseconds or if it is just an arbitrary delay number. I just know that using that little rootdelay hack has worked for a lot of other people who've gotten the same booting error as you, so I thought I would suggest it. :)

---

