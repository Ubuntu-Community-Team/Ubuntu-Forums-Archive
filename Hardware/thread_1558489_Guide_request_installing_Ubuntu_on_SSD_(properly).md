---
title: "Guide request: installing Ubuntu on SSD (properly)"
date: 2010-08-22
forum: Hardware
---

### Post by l3dx on 2010-08-22
Hi,

I've been doing some searching, but I can't find what I'm looking for. I'm just about to start a new installation on a Intel X25-M G2 SSD, and want to do it right. That is, to get the most out of it both performance- and duration wise.

What I've found so far is [this guide over at archlinux forums]("http://wiki.archlinux.org/index.php/Solid_State_Drives"), but it would be nice to something similar for Ubuntu. 

If there is such a ubuntu-specific guide, please tell me :)

---

### Post by clrg on 2010-08-22
Why would you install an operating system on a SSD any differently from a HDD?

---

### Post by l3dx on 2010-08-22
Well, I guess it depends. But from reading the archlinux article it seemed to me that there are a couple of things you would/should do a bit differently. For instance the partition alignment.

I noticed that there are at least one thread for optimizing 10.04 for SSD's, so for me that's good enough for now.

---

### Post by clrg on 2010-08-22
I assume this solved the problem? If so, please mark the thread as solved, thanks.

---

### Post by schmickey on 2010-09-13
"l3dx" is right, there are many things to check, tweak and set properly to get the full performance and longevity from an SSD.  Considering how expensive they are, per GB, we want them to last as long as possible and get full speed from them.

There is some info in [This Thread]("http://ubuntuforums.org/showthread.php?t=1463870") but that information should really be here in the hardware & laptops section because laptop users have some limitations with SSDs that need to be dealt with... i.e., most of us can't use a HDD internally alongside the SSD.

For instance, to use TRIM, you must use the Ext4 FS and only certain kernels support that.  Alignment is critical to performance and small file writes need to be minimized.  A comprehensive guide for installing and maintaining Ubuntu on an SSD would be very helpful.

@l3dx: I am getting the same drive: Intel X25-M G2 80GB and would like to hear how your install went and what settings you changed.

---

### Post by l3dx on 2010-09-13
At the moment I'm most interested in getting the most out of it performance wise. I guess that as the disk gets older, faster, bigger and cheaper disks will appear, so if it works fine for 5+ years, it should be fine by me. I read [here]("http://www.anandtech.com/show/2614/4") that Intel guarantees (though only with a 3yr warranty:P) that you can write 100GB a day for 5 years..

I haven't spent that much time yet, but what I've done is:

[LIST]
[*]
[*]locating /tmp in RAM
[*]/var partition on non-SSD
[*]noatime mount option
[/LIST]

everything is found in the arch linux guide

---

### Post by schmickey on 2010-09-13
I've seen a lot of warnings about partition alignment. Did you create your partition(s) with gparted and uncheck the "round to cylinder" box?

The Arch thread is very helpful but any Ubuntu-specific settings, tweaks and software could be posted here.

As far as longevity, those NAND flash cells can only hold a charge for 10 years.  I'm not worried about wearing it out before then but I definitely want the best speed it can deliver.  Mis-alignment = poor speed.

---

### Post by schmickey on 2010-09-14
For anyone getting an Intel SSD:
There is a very informative video [HERE]("http://intelstudios.edgesuite.net/idf/2009/sf/aep/IDF_2009_MEMS003/f.htm") which you should watch.  This site uses "activeX controls".  I watched it in Windows 7 and had to use Internet Explorer (ugh!) in order to get it to run.  I haven't tried to watch it in Linux.

Leaving at least 10% of your drive unallocated (not within a partition) will increase the lifespan of your drive dramatically, exponentially.  But this is only for brand new drives that have never been used.  If it HAS been used, you have to secure-erase it first to gain this advantage.

---

### Post by movieman on 2010-09-14
> **l3dx said:**
> I haven't spent that much time yet, but what I've done is:

[LIST]
[*]
[*]locating /tmp in RAM
[*]/var partition on non-SSD
[*]noatime mount option
[/LIST]

everything is found in the arch linux guide

I also put /var/tmp, /var/log and the Firefox cache in RAM disk; I have a script that creates /tmp/$USER/cache on boot and then link to that from the Firefox profile.

In theory /var/tmp is supposed to maintain its contents over reboots, but nothing important seems to use it.

---

