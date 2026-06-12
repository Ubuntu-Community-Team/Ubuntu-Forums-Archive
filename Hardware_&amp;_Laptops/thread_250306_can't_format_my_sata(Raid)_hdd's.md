---
title: "can't format my sata(Raid) hdd's"
date: 2006-09-03
forum: Hardware &amp; Laptops
---

### Post by bastupungen on 2006-09-03
Hello!
I have 2 sata disc's that i raid (clone) through the built in chipset in the card. I assign the raid configuration before loading ubuntu.

When i Load Ubuntu, and start Disks though the system menu, I can see all the 3 disks (system and 2 other disks that are cloned). I can see the partitions on the 1 disk (System) and i can see it on the 3 disk, but not on the 2 disk. Though i can't seem to mount them through that panel. So i first try to unpartition and format them cleanly (formating one should do) though parted. But parted cannot operate with them. It says, roughly translated, unknown allocationtable. ](*,) 

Why is this? Can't I use the smart hardware raid configuration within ubuntu, to gain safety and lose strain on the CPU? Do i have to remove the raid config and use an software raid config instead?

The chipset im using is an ALi M5281 Sata/Raid controller.

---

### Post by meng on 2006-09-03
If I understand the problem correctly, perhaps you should try repartitioning/reformating using something like a GParted LiveCD rather than doing it in Ubuntu.

---

### Post by neptune39 on 2006-09-04
At a guess its fake raid, did the raid come on the mother board or on a cheap pci card, if so its probally fake. You can do a software raid using the alternate install disk.

---

### Post by bastupungen on 2006-09-04
Do you think the live CD vill be able to work with the disks better than ubuntu, if so, why?

---

### Post by bastupungen on 2006-09-04
How do you mean fake-raid, and why is that the problem?

---

### Post by neptune39 on 2006-09-04
From what i've read about raid its common for the card you buy or comes on motherboards to just be a sata controller that comes with a disk that is designed to help winxp set up a software raid. If this is the case with you then just use that hardware as  a sata controller and set up a software raid with the alternate install disk, its on the downloads page and says its for unusual installs like with raid.

What kind f raid do you want, raid 0 - one big drive or mirroring raid 1?

---

### Post by meng on 2006-09-04
> **bastupungen said:**
> Do you think the live CD vill be able to work with the disks better than ubuntu, if so, why?
Yes, I suspect so, although I'm not tech-savvy enough to say why. All I know is that I've run into trouble resizing/reformating if I boot into an installed Ubuntu, and often end up with a black-bordered unrecognized partition. Whereas using the GParted LiveCD, that doesn't happen (even though they seem to use the same program).

---

### Post by neptune39 on 2006-09-04
I think only the alternate install disk supports software raids during setup, its actually quite easy to do, get the cd and try it, if you run into trouble just ask.

---

### Post by bastupungen on 2006-09-04
> **neptune39 said:**
> From what i've read about raid its common for the card you buy or comes on motherboards to just be a sata controller that comes with a disk that is designed to help winxp set up a software raid. If this is the case with you then just use that hardware as  a sata controller and set up a software raid with the alternate install disk, its on the downloads page and says its for unusual installs like with raid.

What kind f raid do you want, raid 0 - one big drive or mirroring raid 1?

I assign the raid config from the startup system(right after Bios), soo i don't think its a software raid.

I want a clone raid so i guess thats raid 1

---

### Post by bastupungen on 2006-09-04
> **meng said:**
> Yes, I suspect so, although I'm not tech-savvy enough to say why. All I know is that I've run into trouble resizing/reformating if I boot into an installed Ubuntu, and often end up with a black-bordered unrecognized partition. Whereas using the GParted LiveCD, that doesn't happen (even though they seem to use the same program).

Seems wierd.. i guess i have to try too find a liveCD somewhere and try that... If all other options fail, that is.

---

### Post by neptune39 on 2006-09-04
Some fake raid controllers are set up through bios so that isn't proof that its not a fake raid card, as in its just a software raid. If you were to install windows it would work fine but it doesn't work with linux as easy. Youre best bet is the alternate install CD which will let you set up a software raid 1. the regular live cd will not. If the card is not true hardware raid, think $200+ then a software raid through the install disk will be the best solution. Below is the CD image you need to download:

[http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/ubuntu-6.06.1-alternate-i386.iso](http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/ubuntu-6.06.1-alternate-i386.iso)

Heres a link on fake raid:

[http://linux-ata.org/faq-sata-raid.html](http://linux-ata.org/faq-sata-raid.html)

You might have to turn off the raid you have to do what Im talking about.

---

### Post by vva on 2007-07-21
Hi,

Has this issue been resolved? I tried to install Kubuntu 7.04 on my system, which probably has the same chipset ALi/ULi M5281 and I got an error when trying to resize my ntfs partition. This worried me enough so I didn't insisit and winXP was able to repair the damage on boot.

I'm using neither hard- nor software RAID. The controller is only there for my SATA drive.

I downloaded the Red Hat driver (old) from ULi but I'm newbie enough not to be able to figure out whether/how to apply the instructions to installing Kubuntu from the live CD. Should I use the alternate CD and how?

Or would GParted LiveCD do the trick?

I'd hate to wipe out my windows partition in the process... Been there.

r. Ville Valtasaari

---

