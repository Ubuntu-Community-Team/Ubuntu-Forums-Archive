---
title: "Help with removal of linux for fresh ubuntu install"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by redbullman on 2009-01-09
Hi there

I wonder if you can help.   I’ve tried out a variety of difference linux distros of the last couple of months to decide which I prefer.  First of all I had a dual boot with Vista Ultimate and Ubuntu 8.10 32 bit.  Then I tried Fedora 10 64 bit dual boot, then OpenSuse 11.1 64 bit dual boot.   I created the initial partition with Windows and the dual boot set up when installing Ubuntu 8.10 32 bit.

I have selected the guided installs with all installs so far and had no problems.  However, I’ve now gone back to Ubuntu 8.10 (this time 64 bit).  It installed fine.  I selected guided install again as I’m no partitioning expert.  However on the Grub menu, it appears to show Vista, Ubuntu and OpenSuse.  So basically it didn’t get rid of Opensuse when installing Ubuntu.

I think the best option is removing all traces of Linux (Ubuntu and OpenSuse), leaving just the original Vista install.  I can then run the Ubuntu installer using the guided install so everything is set up automatically.

So my question is, what’s the best way to remove all traces of Linux (Ubuntu and OpenSuse), to enable a fresh install of Ubuntu alongside my existing Vista install?

I initially thought I would be able to delete all Linux partitions through Vista admin tools.  However I understand Windows can’t read the Ext3 file structure.

Really appreciate some help here!

Thanks

---

### Post by caljohnsmith on 2009-01-09
If you want, from the Live CD you could open the partition editor (System > Admin > Partition Editor) and use that to delete all your linux partitions. That should remove all traces of linux except if you have Grub in the MBR (Master Boot Record) of the HDD, but since you plan on reinstalling linux anyway, that should not be a problem. Good luck and let me know how it goes. :)

---

### Post by donkyhotay on 2009-01-09
Personally I just reformat on the rare times I need to wipe out ubuntu and start over again. Unless you are actually changing your partition sizes there isn't much reason to go through repartitioning since they are already configured.

---

