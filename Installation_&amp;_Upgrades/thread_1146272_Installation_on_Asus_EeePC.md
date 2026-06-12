---
title: "Installation on Asus EeePC"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by TKMR on 2009-05-02
Recently one of my friends decided he wanted to install Ubuntu on his netbook, I told him I would help him out. I downloaded the netbook remix version and got everything onto a flash drive and then started to go through the install process. When I got to the Partitioning stage of the install, I discovered that there were 4 partitions on his Hard Drive. SDA1/2 were both in windows with SDA1 being used for "System files" and SDA2 being used for user files (although there was nothing on SDA2, and everything including his "user files" is on SDA1). SDA3/4 are both small partitions, 8GB and 2GB respectively. I attempted to do some research on what was on these two partitions. Some places said that SDA3 (8GB) was a recovery partition that had all of the system-restore information on it, and SDA4 was a "Bios" partition that stored all the information regarding the Bios. 

What I am worried about is that if I completely wipe the HDD in his netbook he won't be able to access the Bios, or boot the computer, and if something does go wrong with the computer he won't be able to restore the system (it came with XP). I also can't reformat SDA2 to EXT3/4 because, I'm assuming, that SDA3/4 come after it on the HDD and Ubuntu won't install between two partitions.

I'm at a loss for what to do. He does want to dual boot XP/Ubuntu Remix. Can anybody clarify what SDA3/4 are for, and if it is ok to reformat them?

I believe he is using the Asus EeePC 1000H model. Asus' site wasn't a big help on this, and neither is his User manual.

---

### Post by snowpine on 2009-05-02
My eee 900ha had a similar partitioning scheme. I deleted sda2 (the empty D: partition) using gparted, and then ran the installer and selected the option to install Ubuntu in the free space. I am dual booting Ubuntu and Windows no problem.

---

### Post by TKMR on 2009-05-02
I tried doing that and the installer wouldn't let me format and install to that partition. It was considered unusable space. =/

---

### Post by snowpine on 2009-05-02
If I remember correctly, the problem is that a hard drive can only have 4 primary partitions. So you have to delete sda2 (using gparted) before running the installer. The installer is smart enough to set up a logical/extended partition scheme if there are 3 primary partitions and an empty space.

---

### Post by TKMR on 2009-05-02
Alright. He should be coming by later today, so I'll try that.

Thank you for the help. If that doesn't work I will report back.

---

### Post by TKMR on 2009-05-06
That worked, thank you very much!

---

### Post by tmt1096 on 2009-07-16
The other option is to install Ubuntu on a SD.
Installed 9.04 on an 8Gb SD (also works with 4Gb) and just dual boot from BIOS menu.
Note: You have to boot from a USB flash.

I have now removed the internal SATA an just boot Ubuntu from SD.
I now have everything I need except Windows Live Messenger (for Video conference).

tmt1096

---

