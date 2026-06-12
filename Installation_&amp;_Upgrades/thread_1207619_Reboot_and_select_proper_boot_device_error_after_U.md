---
title: "Reboot and select proper boot device error after UBUNTU UNINSTALL. Need help"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by curiousDood on 2009-07-08
I had ubuntu and WinXp on the same 40gb IDE PATA HD in different partitions. I bought a new 320gb SATA HD. I wanted to install ubuntu to the new SATA. I uninstalled it by using 'install ubuntu' and reducing the partition space tht ubuntu previously had to 0, and went to sytem>administrator>partitioiner and checked and made sure all space was returned to XP. Then I used FixMbr to fix the MBR of XP. But when I rebooted I got this "Reboot and Select Proper Boot Device or insert boot disk..."error. I looked in lots of places, but the only idea I got was that it might be a MotherBoard Memory limit or something. I use an AsRock Prescott 800 MB. The Funny thing was my old HD, the new 320gb SATA and a friends 80gb all worked well before the uninstall. will be grateful for any advice.

here's what i did:


1.I uninstalled ubuntu
2. fixed MBR
3.connected both HDs but got 'reboot and select proper boot device error'
4.BIOS is detecting both Hds
5.WinXp cd in restore mode says my old IDE is invalid
but shows partitions and memory
fixboot, fixmbr, bootcfg wont work

---

### Post by presence1960 on 2009-07-08
I would have removed your ubuntu by booting the live CD and using gparted to delete the partition, of course back up files first! Then you could have extended windows partition to include the unallocated space created by removing the ubuntu partition. I have never heard of doing what you just did, but maybe I am incorrect in thinking that is not the way to remove ubuntu.

---

### Post by curiousDood on 2009-07-09
Obviously I'm a newbie :) 

I got the problem solved though...the hard way. I formatted my new 320gb SATA and made it a basic disk. My XP had a problem with recognizing dynamic disks. Now i have ample space to try out new softwares and install and meddle with Ubuntu again :). I searched everywhere for a solution, but what you gave was a straight forward solution. Thanks for the reply.

---

