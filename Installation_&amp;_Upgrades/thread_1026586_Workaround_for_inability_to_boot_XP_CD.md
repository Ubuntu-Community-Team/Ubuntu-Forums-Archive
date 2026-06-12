---
title: "Workaround for inability to boot XP CD"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by xelxel on 2008-12-31
I'm sitting at my parents place dumbfounded with this problem. They want to revert to windows due to some driver issues with a router, and i got my hands on a windows xp CD. I insert it into laptop CD Tray, and reboot.

It refuses to boot from that particular CD. I have tried with Ubuntu, Xubuntu and even Kubuntu CD's and it boots/installs just fine. At first thought i assumed it was an incompatibility issue between the file systems, so i created a minimal partition with ext3 to install ubuntu and a larger one as FAT32, but still no luck to boot from the xp CD. This i did during the pre-installationsteps.

I had the identical issue on my own laptop a while ago, but i couldn't for the life of me remember how i resolved it.

Does anyone here have any suggestions on how to proceed/troubleshoot this?

//Erik

---

### Post by hansdown on 2008-12-31
Hi xelxel.

You need to fix the master boot record to re-install xp.

[http://fixunix.com/ubuntu/254674-re-installing-windows-after-ubuntu-installation.html](http://fixunix.com/ubuntu/254674-re-installing-windows-after-ubuntu-installation.html)

---

### Post by oilchangeguy on 2008-12-31
> **hansdown said:**
> Hi xelxel.

You need to fix the master boot record to re-install xp.

[http://fixunix.com/ubuntu/254674-re-installing-windows-after-ubuntu-installation.html](http://fixunix.com/ubuntu/254674-re-installing-windows-after-ubuntu-installation.html)

the op does not need to fix the master boot record of anything, in order to be able to boot from a cd. which is the op's problem. the computer refuses to boot from the cd. op, have you tried the cd in another computer? and please give a detailed description of what happens when you try to boot in the computer giving you problems.

---

### Post by xelxel on 2008-12-31
> **oilchangeguy said:**
> the op does not need to fix the master boot record of anything, in order to be able to boot from a cd. which is the op's problem. the computer refuses to boot from the cd. op, have you tried the cd in another computer? and please give a detailed description of what happens when you try to boot in the computer giving you problems.

I have the identical problem with my own laptop and xp CD's. The Laptop boots, displaying GRUB [countdown] then ubuntu loads as if there were no CD at all in the tray. No errors, no "Press any key to continue", no nothing =(

---

### Post by y@w on 2008-12-31
> **xelxel said:**
> I have the identical problem with my own laptop and xp CD's. The Laptop boots, displaying GRUB [countdown] then ubuntu loads as if there were no CD at all in the tray. No errors, no "Press any key to continue", no nothing =(

And you said it boots off Linux live CDs? It sounds to me like you just need to change the boot order in BIOS.

---

### Post by oilchangeguy on 2008-12-31
> **xelxel said:**
> I have the identical problem with my own laptop and xp CD's. The Laptop boots, displaying GRUB [countdown] then ubuntu loads as if there were no CD at all in the tray. No errors, no "Press any key to continue", no nothing =(

is the computer(s) set to boot from the cd drive first? is the cd undamaged? is the cd drive working? do you have a lens cleaner cd?

---

### Post by melojo on 2008-12-31
If the laptop can boot ubuntu cd's and not the xp cd then it has to be the xp cd.  I would try to find another and give it a try.

---

### Post by xelxel on 2008-12-31
> is the computer(s) set to boot from the cd drive first? is the cd undamaged? is the cd drive working? do you have a lens cleaner cd?

> If the laptop can boot ubuntu cd's and not the xp cd then it has to be the xp cd. I would try to find another and give it a try.

That's the funny thing, ubuntu CD boots fine so i can't imagine how BIOS would differentiate between these two CD's. I have two different windows xp CD's. One is my own, and the other is one that my parents aquired. I have tried both on my own laptop (I figured that xp might not provide working ethernet drivers so i brought my laptop to DL drivers for theirs) as well as theirs and it refuses to boot on either laptop. 

Alternatively, is it possible to copy over the files to a flash memory stick and use that as installation source? I have an 8GB one which obviously is more then enough for xp 32bit.

---

### Post by melojo on 2008-12-31
> **xelxel said:**
> That's the funny thing, ubuntu CD boots fine so i can't imagine how BIOS would differentiate between these two CD's. I have two different windows xp CD's. One is my own, and the other is one that my parents aquired. I have tried both on my own laptop (I figured that xp might not provide working ethernet drivers so i brought my laptop to DL drivers for theirs) as well as theirs and it refuses to boot on either laptop. 

Alternatively, is it possible to copy over the files to a flash memory stick and use that as installation source? I have an 8GB one which obviously is more then enough for xp 32bit.

Are you saying that both xp cd's fail to boot on both systems?

---

### Post by xelxel on 2008-12-31
> Are you saying that both xp cd's fail to boot on both systems? 

Indeed! See my confusion over this? Had it been one CD, i would've suspected a bad burn or scratches or some other form of disc damage/data corruption, but since neither will boot the xp installation there's something fishy going on. My primary suspect is the file system. Using whatever the heck is normal from when installing and using the entire HDD for ubuntu, i figured it might cause the windows CD to be unable to read/manage/create whatever it needs on the HDD to launch the installation.

I know i have had this issue once before and solved it, but it was ages ago and i think i was using Fedora at the time and installing xubuntu solved it. The party pooper is that my parents are using xubuntu and it didn't work there.

---

### Post by oilchangeguy on 2008-12-31
> **xelxel said:**
> Indeed! See my confusion over this? Had it been one CD, i would've suspected a bad burn or scratches or some other form of disc damage/data corruption, but since neither will boot the xp installation there's something fishy going on. My primary suspect is the file system. Using whatever the heck is normal from when installing and using the entire HDD for ubuntu, i figured it might cause the windows CD to be unable to read/manage/create whatever it needs on the HDD to launch the installation.

I know i have had this issue once before and solved it, but it was ages ago and i think i was using Fedora at the time and installing xubuntu solved it. The party pooper is that my parents are using xubuntu and it didn't work there.

the hard drive will not stop the computer from being booted from the cd drive. when you are running the computer from a cd, the hard drive is not involved. how far does the computer get when you boot it from a windows cd?

---

### Post by xelxel on 2008-12-31
> **oilchangeguy said:**
> the hard drive will not stop the computer from being booted from the cd drive. when you are running the computer from a cd, the hard drive is not involved. how far does the computer get when you boot it from a windows cd?

It ignores the windows xp and continues on to load ubuntu as if there were no CD in the tray at all.

---

### Post by melojo on 2008-12-31
> **oilchangeguy said:**
> the hard drive will not stop the computer from being booted from the cd drive. when you are running the computer from a cd, the hard drive is not involved. how far does the computer get when you boot it from a windows cd?


+1

Take the hd out then and try it again if you suspect that is the problem, but I am in agreement with oilchangeguy. When booting from the cd it bypasses the hd boot and file system.

---

### Post by xelxel on 2008-12-31
I'd rather not start picking out the parts of two laptops, especially since i'm the walking definition of clutz. If these are unrelated, then i'll go with that line of thought. Pretty much everyone is more well versed regarding computers then me :)

---

