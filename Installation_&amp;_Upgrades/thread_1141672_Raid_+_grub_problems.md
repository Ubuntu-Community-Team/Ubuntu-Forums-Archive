---
title: "Raid + grub problems"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by ashakeandfrys on 2009-04-28
I've installed Ubuntu before on a 160GB drive and the Ubuntu partition was after windows.. no problem. This set up was on a single IDE drive.

I now have two SATA drives in RAID and installed Ubuntu on the disk's using dmraid. Every time I try to install grub I get errors such as 15 and 18; something about cylinders exceeding the max supported by the bios.

I tried following the FakeRaidHowTo, but whenever I get to the part about installing grub I get errors as if it's not installed. I've read somewhere that you have to install before the 1024th cylinder.. but I've installed past that on the 160GB drive.

How did you get yours to install on a raid setup?

---

### Post by ashakeandfrys on 2009-05-01
I have solved the problem. Ubuntu was referencing one of my IDE drives instead of the raid array. I unplugged the IDE music drive and GRUB installed fine and sees both Ubuntu and Windows. 

ext4 makes a HUGE difference in boot times..

---

