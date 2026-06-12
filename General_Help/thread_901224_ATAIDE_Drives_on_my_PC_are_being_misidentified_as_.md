---
title: "ATA/IDE Drives on my PC are being misidentified as SCSI"
date: 2008-08-26
forum: General Help
---

### Post by WolvenSpectre on 2008-08-26
I have an older secondary PC which has 2 Western Digital IDE/ATA drives.  Upon a first install of 8.04, and every install ever since, Ubuntu keeps saying that my 40 GB Master and 30 GB Slave are SCSI.  It will install, format, and partition the drives but will not allow me to change the name, share them, or alter the permissions to those drives.

I tried Live, OEM, and straight installs and nothing helped.

I did update the system and rebooted before trying.

I am using an ASUS A7V Mobo, Ti 4200 Nvidia video card, SB16 audio, 1 GHz Athlon CPU, 768 MB PC100 RAM.  On the primary IDE channel I have the 2 Drives and a CD Burner and DVD-Rom on the secondary channel. 

I did not have these problems with prior versions of Ubuntu and Kubuntu in the same machine.  I have both used it to get more familiar with the GUIs and as an ersatz NAS.

please keep in mind when talking about the command line to speak slowly and clearly as my IQ drops about 40 pts when I converse on that topic due to a condition called utter noobosis.

So... any Ideas?!?!

---

### Post by coffeecat on 2008-08-26
I should imagine that when you say Ubuntu is telling you that your ide drives are scsi, it's because it's now calling them sda and sdb, not hda and hdb. Don't worry, that's quite OK. It's because of a change in the kernel ata drivers. There used to be separate ones for all the different types of drives and, with the older drivers, scsi and sata drives were called sdx and ata/ide were called hdx.

The newer kernel drivers (the libata drivers) handle all types of drives and allocate the descriptor sdx to all. It has taken some time for all makes of drive controller to be included in the libata drivers, which is why some people have seen this change before others.

I'll try to find a link a post again if I do.

---

### Post by coffeecat on 2008-08-26
I found the link quicker than I thought I would. It's a bit old and refers to the change that came in with the 2.6.19 kernel. We're now up to 2.6.24 in Ubuntu. [This is the link]("http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce").

I've just re-read your post.

> **WolvenSpectre said:**
> It will install, format, and partition the drives but will not allow me to change the name, share them, or alter the permissions to those drives.

Apologies for missing that. What specific share and permission problems were you having?

---

### Post by Too Late on 2008-08-26
I have two parallel ATA drives, too. One is primary master and the other is secondary master. During the installation, Ubuntu called them as "SCSI3 (0,0,0) (sda)" and "SCSI4 (0,0,0) (sdb)" respectively. In my opinion, that didn't look very nice. However, I haven't had any other problems, like permissions etc. So I think your problems have nothing to do with this naming thing.

---

### Post by Garratt on 2008-08-26
yea same deal, i have 1 iDE, 1 SATA, and it called them both SCS on install

---

