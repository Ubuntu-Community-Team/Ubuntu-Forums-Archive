---
title: "Abit KT7-RAID"
date: 2006-10-10
forum: Hardware &amp; Laptops
---

### Post by RamonBianco on 2006-10-10
Greetings, all.

I am trying to install Dapper Drake on my KT7-RAID, and I am not having any luck.

The only PCI cards I have installed are a Linksys 10/100 card and a Turtle Beach Santa Cruz sound card.  I have a couple of CD/RW drives in the regular IDE connectors, a couple of old hard drives on one connector of the RAID controller, and a new 100 GB drive on the other connector (no RAIDing of any kind, just separate disks).

I installed from the CD, which ran okay, and I chose to use the whole new drive only for the install.  But when I reboot, it goes into "infinite reboot" mode.  It goes through the BIOS boot screen, then the HighPoint boot screen, detecting all the drives, then immediately reboots.

I would appreciate any help on this problem.

Thanks.

---

### Post by RamonBianco on 2006-10-17
I was able to install the OS on the new drive and get it to the point of functionality.

Unfortunately, the OS was Windows 98SE.

I have tried various options in the Dapper install, but nothing seems to work.

My latest attempt was to disconnect all of the hard drives except the new one, on the first RAID port, using the whole drive after clearing it.  The install stalled at 53%.

---

### Post by richarddavidlee on 2007-03-18
I have got the same problems, install works fine, reboot the pc for the first time with the new OS   and I get the infinite reboot problem. 

The last thing I see flash up on screen for a microsecond before the reset is something like "Grub" its hard to make out cause its only of for such a short time, don't know if that means anything to anyone?

I have tried installing on a 20gb maxtor and a 40gb seagate barracuda, the reboot happens at the same point on either disk.

edit:

I just found out some info which may/may not help, havn't tried it yet but here is the link ([https://launchpad.net/ubuntu/+source/grub/+bug/8978](https://launchpad.net/ubuntu/+source/grub/+bug/8978))

---

