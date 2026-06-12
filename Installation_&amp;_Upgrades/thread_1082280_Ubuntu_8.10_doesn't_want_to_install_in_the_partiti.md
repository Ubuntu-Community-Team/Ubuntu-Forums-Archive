---
title: "Ubuntu 8.10 doesn't want to install in the partition I want."
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by TexMachina on 2009-02-27
OK, I have a work laptop with XP and I wanted to use the remaining 20GB of unpartitioned space for an Ubuntu install. Problem is the installation's partitioner just wants to either re-size my existing partition or flatten the whole machine. It sees the unused space, but I see no way of forcing it to use the unused space. 

To get around this I manually created the ext2 partition and a swap partition before restarting my install. Now the install wants to re-size ALL of the partitions. How do I run the 8.10 desktop installation without it touching my very important, work related, could get into a world of **** if it is corrupted NTFS partition?

God I hate it when computer programs are idiot proofed to the point of uselessness like this.

---

### Post by anjpr on 2009-02-27
The problem is that you are formatting the free space as an ext2 partition when it should be an ext3 partition.  If the LiveCD doesn't work for you download gparted at gparted.sourceforge.net/, burn an iso image and do the formatting with it.

---

### Post by wpshooter on 2009-02-27
My advice is that if you do not have authorization to do this, then do NOT attempt to do it at all !!!

---

### Post by TexMachina on 2009-02-27
Well using ext3 didn't work. It still insists on resizing partitions. 

You know what. To hell with this. I'm sick of these slicked up cutesy name distros. I'm going back to Slackware. It may be a whore to install but I'd rather wrestle with technical issues than a retard ******* install wizard.

---

### Post by jerrylamos on 2009-02-27
> **TexMachina said:**
> Well using ext3 didn't work. It still insists on resizing partitions. 

You know what. To hell with this. I'm sick of these slicked up cutesy name distros. I'm going back to Slackware. It may be a whore to install but I'd rather wrestle with technical issues than a retard ******* install wizard.

On Ubuntu partition screen, just select manual install.  You can pick what partition you want for what.  If you want to resize or new or whatever, use gparted first from live CD.

Jerry

---

