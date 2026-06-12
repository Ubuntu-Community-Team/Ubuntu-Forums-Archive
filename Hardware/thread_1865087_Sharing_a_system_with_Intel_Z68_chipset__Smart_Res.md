---
title: "Sharing a system with Intel Z68 chipset / Smart Response Technology"
date: 2011-10-19
forum: Hardware
---

### Post by tobestool on 2011-10-19
Hi,

I've just bought a new SSD to speed up my system, partly due to the fact that my recent motherboard (an Asus P8Z68-V) has built in support for using a solid state drive as a cache of a mechanical drive. I also have two 1TB Hitachi drives in my system. I have now got Windows 7 installed and have enabled the caching using 64GB of the new SSD.

I would now like to use the remaining space on the SSD for an Ubuntu system partition, probably with partitions on the mechanical drives used for areas such as /srv and /home. However I'm getting nowhere getting this installed. I've previously been working on this motherboard with Xubunu and Ubuntu Studio 11.04, however this fails to install grub, complaining that it can't access /dev/md127. I've tried installing with a Xubuntu 11.10 disc, which will install to the mechanical drive, however does not offer me the SSD during the installation. It also fails to add the Windows installation to the Grub menu.

Does anyone have any experience with this feature of Intel's latest chipset? I'm keen to give my Linux install a performance boost with the new drive as well as the Windows system...

---

### Post by Rich.T. on 2012-03-03
I'm having much the same problem.

I'm currently trying in vain to install Ubuntu 12.04 on the 47GB RAID volume left spare on my 112GB SSD, by using dmraid to detect and mount it, thus giving me a dual-boot system: the RAID volumes are detected, but not the partitions within.

This would appear to be a falure within dmraid.

Perhaps the fact that this controller creates a RAID0 "array", actually consisting of a single volume is causing dmraid to break or mis-report, or something.

Am I wrong?

Would anyone here with experience of using dmraid for installations care to add to this?

I managed to set up and run a dual-boot system with Windows Vista and Gutsy a couple of years ago, with everything running from a single (Intel) RAID0, broken up into 3 volumes, each sub-partitioned.

---

### Post by Rich.T. on 2012-03-03
UPDATE:

Forget all of that.

I just got Mythbuntu 11.10 to install to the 48GB ISW volume.

My problem was one which seems to affect many people:

Through my experimenting with many setup variants; I had previously setup my SSD as GPT - In point of fact, a previous install of Ubuntu had automatically launched from it's USB drive via it's UEFI boot function through BIOS, initiating an EFI install and GPT format.

I subsequently reformatted through Windows, which thoroughly screwed up the GPT tables. As has been explored elsewhere, Windows does not follow the specifications of this disk system and gparted does not like this one little bit.

Basically, I de-RAIDed the drive through option-ROM BIOS, re-initiallised the full drive again through gparted (properly), set up the Smart Response "array" through Intel's windows software again, executed [dmraid -ay], initialised the 47GB volume through gparted and then finally ran the Ubuntu installer again, this time with success.

I hope this helps anyone who may stumble across this thread in their desparation, just as I did.

---

