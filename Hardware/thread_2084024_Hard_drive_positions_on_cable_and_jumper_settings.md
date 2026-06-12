---
title: "Hard drive positions on cable and jumper settings"
date: 2012-11-14
forum: Hardware
---

### Post by welshmike on 2012-11-14
I want to install Ubuntu on a friend of mine's Dell desktop PC that he inhered from his son who we are not able to contact. The PC is running a very sluggish Windows XP.
The PC has two PATA HDDs.
One HDD of 40GB is positioned at the end of the signal cable the other 150GB HDD is in the middle.
The 40GB HDD is jumpered (I believe on pins 7&8 and 5&6). The 150GB HDD is not.
I have booted with an Ubuntu live CD and Gparted shows that the middle drive is boot. Both drives have Windows systems installed on them and user data is on the 40GB end drive. I do not know what Windows system is booted and used but the data accessed in on the 40GB HDD.
I would like advice please on where I should position the drives on the signal cable and what jumper settings are needed.

(An afterthought. I could of course remove the 40GB HDD and put the 150GB HDD on the end of the cable. What jumper settings then please?)
(Second afterthought. Jumper settings 7&8 I believe)

---

### Post by ahallubuntu on 2012-11-14
There is no standard for PATA hard drive jumper numbers.  I have no idea what pins 7-8 and 5-6 mean - it is completely different on every make and model of drive.

You should be able to find a key on every individual drive for how to set the jumpers to get a specific setting.  There are three standard settings: Master, Slave, and Cable Select (CS).  If you set each drive to Cable Select, the position on the cable (which connector) determines whether it is the Master drive or the Slave drive on the cable.  If you want choose them yourself no matter where the drive is on the cable, set one drive to Master, one to Slave.  Sometimes a bit of trial and error is required; I have seen some drives that do not talk well with the drive controller when set to CS vs. Master and vice versa.

If you don't want to remove the drives physically to find out how to set the jumpers (from the key on the drive label), you'll have to figure out the manufacturers and the model numbers and try googling them to find out the jumper block keys so you can correctly set master and slave or CS.

---

### Post by welshmike on 2012-11-14
Thank you for the info.

---

### Post by Yellow Pasque on 2012-11-14
> **ahallubuntu said:**
> If you want choose them yourself no matter where the drive is on the cable, set one drive to Master, one to Slave.
IIRC, the one on the end should be Master and the "middle" one should be Slave. Also, make sure you're using a flat, 80-pin cable, preferably as short as possible.
Cable Select is the slacker way out and sometimes, it's better to set Master/Slave yourself.

---

### Post by oldfred on 2012-11-14
If you have the 80 conductor cable then you can use cable select. If not you have to set drives to master & slave. 
If you have cable select then BIOS will let you select boot drive.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by welshmike on 2012-11-14
What has got me confused is that Gparted indicated that the drive in the middle of the cable was boot.
The data used by Windows XP was on the drive on the end of the cable. Also as I wrote before, both drives had XP installed on them.
Does XP have to be on the drive that is boot?

---

### Post by oldfred on 2012-11-14
If gparted is showing boot that is just the boot flag.

BIOS boots from MBR, Windows boot loader in the MBR looks at partition table for primary partition with boot flag and jumps to that partition's PBR - partition boot sector to continue with more Windows boot code.

So every drive with Windows should have a boot flag (and had to, to be installed). But older BIOS could only boot from primary channel's master drive. Newer BIOS let you choose which drive is bootable, but that is in BIOS not a flag on the partition.

---

### Post by welshmike on 2012-11-15
> **oldfred said:**
> 

BIOS boots from MBR, Windows boot loader in the MBR looks at partition table for primary partition with boot flag and jumps to that partition's PBR - partition boot sector to continue with more Windows boot code.


Thanks again for explaining.
Sorry to prolong this but am I correct in understanding that Windows MBR, PBR, boot code and Operating System must all be on the same physical drive?

(EDIT) I'm considering removing the 40GB drive that is on the end of the data cable and using only the 150GB drive that is in the middle of the cable. Is the middle the correct place when just a single drive is used?

---

### Post by oldfred on 2012-11-15
If you have the cable select 80 conductor cable (colored ends, not just grey) and a BIOS that lets you choose boot drive then it does not matter. But with cable select the jumpers must be cable select.

Otherwise what matters is the jumpers, the boot drive must be set to master and usually on the primary channel.

---

