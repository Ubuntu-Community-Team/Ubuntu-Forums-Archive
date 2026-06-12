---
title: "Running LiveCD Doesnt Work"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by RizziNUp on 2006-01-31
Hey. Im  a Windows XP Pro user that wants to switch to Linux, and I wanted to try the Linux Ubuntu Live CD to see how it is. Well, I downloaded the LiveCD and followed the instructions, and I end up loading the Ubuntu, but I get a brown background with the Ubuntu Logo in the middle, but it is deformed with static and blur. Kind of strange. I do not know what may be the problem but I will list my computer hardware because it might be the problem?

AMD Athlon64 3200+
EVGA Motherboard
EVGA nVidia 7800GT 256MB
2GB OCZ PC3200 RAM
2 x 80GB Seagate SATA (RAID0)
Onboard Sound
19" LCD

Could it be the raid hdd's? I wouldnt think so because the OS is supposed to be running from the CD, correct? I tried multiple times to start, even at different resolutions, but to no avail. Anyone know what my problem could be? Oh and I downloaded the 64bit version (AMD64).

Mike

---

### Post by aysiu on 2006-01-31
Maybe try the x86 version?
Or, when it's at the brown screen, try Control-Alt-F1 and then ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by RizziNUp on 2006-01-31
Ok. Ill try the brown screen first, then ill try downloading the x86 version.

---

### Post by RizziNUp on 2006-01-31
I downloaded Linux Mepis, and it ran on LiveCD, but Ubuntu hasnt. I will try to now download the x86 version.

---

### Post by RizziNUp on 2006-01-31
I downloaded the x86 version, and the same thing happens. I am thinking that maybe it is the graphics card..? Also, when i hit ctrl+alt+f1, nothing happened. I dont know what to do. I really want to give ubuntu a try.

---

### Post by aysiu on 2006-02-01
The other thing is that maybe it's a bum CD. Even though [I'm in the minority opinion that Ubuntu is overrepresented in the corrupted disks area](http://www.ubuntuforums.org/showthread.php?t=113925), I still stand by what I've experienced myself and witnessed on these forums.

A lot of times the ISO gets corrupted during download, and even the official ShipIt CDs can be corrupt and unusable.

---

