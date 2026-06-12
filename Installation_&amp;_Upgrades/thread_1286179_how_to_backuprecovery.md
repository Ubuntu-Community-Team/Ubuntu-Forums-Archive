---
title: "how to backup/recovery"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by attilab on 2009-10-08
Hm...in windows its called make a system backup for the case if needs a recovery...
I am still with my dual boot (XP/Ubuntu), I need to work with XP and for browsing and fun using ubuntu. Just finishing a recent Fdisk (C and D partitions for XP and a portion of a disk in RAW, here comes the ubuntu). These reformating started making me tired, need a good 24 hour hassle to bring all up back to my taste.
Need a recommendation for a program/software what can make the image of the entire W.XP installed drives what I could save to an external HDD and bring back/recover with push of a button as needed, that means no OS is healthy or operational !!. 
I know that Acronis or GenieBackupManager can do windows, but what about ubuntu? How I could do (backup/recover) a complete dual boot, both systems? it would be a large file but plenty of space on WD Passport.
That would be nice if I could handle this in one button stroke.

---

### Post by mikewhatever on 2009-10-08
I don't know of a one click solution, but have used Partimage recently. It was relatively easy to learn and worked very well for me.

---

### Post by attilab on 2009-10-08
> **mikewhatever said:**
> I don't know of a one click solution, but have used Partimage recently. It was relatively easy to learn and worked very well for me.

I see it is not picking up the empty blocks and that is good, don't need to prepare the same size partition to copy the data over. Good to copy the "C" and "D" and "whatever" partitions to a new but bigger HDD. but asking from a first hand, what it will do with MBR, I mean dual boot?

---

### Post by mikewhatever on 2009-10-08
I believe the MBR is copied along with the data. I haven't had a chance to test that, since I backed up the existing Ubuntu installation (not the first partition), then installed another OS with its own boot loader, and then restored Ubuntu from the backup. To get the bootloader back to MBR, I just reinstalled it.
I am no backup expert, but it was rather impressive. The backup images were rather small, about half the actual data size, because the data is compressed.

---

### Post by attilab on 2009-10-08
my case is oposite, the XP is the first install and that takes long time to fill up. the ubuntu takes max 30 minutes?
either side, the =microsoft based programs and the other=linux based programs taslking about their own features but no cross referencing.
my best guess many XP recoveries will be in my way till the ubuntu is still there, so I have to learn how to put the dualboot=GUI back. searching forums, but not getting things easy.

---

