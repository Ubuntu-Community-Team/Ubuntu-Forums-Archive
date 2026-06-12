---
title: "Upgrade Failed: Hash Sum Mismatch"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by MadDawg010 on 2009-04-21
I am trying to upgrade from either Hardy Heron or Intrepid Ibex (sorry, I did not check which one) using the ubuntu-9.04-rc-alternate-i386.iso image from [http://mirrors.us.kernel.org/ubuntu-releases/jaunty/](http://mirrors.us.kernel.org/ubuntu-releases/jaunty/). When I mount the image and do this command: 

> gksu "sh /cdrom/cdromupgrade"

The installer comes up and apparently fetches the same packages three times, then it finally fails with this error:

> Could not download the upgrades. The upgrade is now aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.

Failed to fetch cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release Candidate i386 (20090414.1)]/pool/main/a/app-install-data-ubuntu/app-install-data_0.7.5_all.deb Hash Sum mismatch

Failed to fetch cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release Candidate i386 (20090414.1)]/pool/main/g/gcalctool/gcalctool_5.26.0-0ubuntu1_i386.deb Hash Sum mismatch

I would simply perform a network update, but for some reason, Ubuntu doesn't seem to like my network card anymore, therefore it will not let me connect to the Internet, or even my own router/network.

I am on a ThinkPad R51e with an 11b/g Wireless LAN Mini PCI Adapter and a Broadcom NetXtreme Fast Ethernet card.

I am dual booting with Windows XP. Partitions are NTFS, FAT, and ext3.

I doubt this would matter, but the iso image is on my Windows partition. I can't copy it because my HDD my be damaged, and it will not copy large files across partitions, no matter which OS I use to copy the image.

Any suggestions?

---

### Post by zvacet on 2009-04-21
First you must know which version you are runing.Type in terminal

```
lsb_release -a

```

If you are running hardy then you will not be able to upgrade to Jaunty.Did you checked [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") before tried to upgrade?If everything is O.K. why don´t you burn iso to CD and then upgrade?

---

### Post by MadDawg010 on 2009-04-21
Thanks. [s]but after reviewing the hash list, I could not find the Jaunty release candidate hash.[/s]

Never mind, I found another list. Thanks again, I'll do this now.

As for burning a CD, I only have one CD left and I'm waiting for the full release Live CD. [s]If the list is updated by then,[/s] I'll use md5sum to check it.

---

