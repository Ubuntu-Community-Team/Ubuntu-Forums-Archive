---
title: "Installing Ubuntu 8.10 for RAID-1 system"
date: 2008-12-09
forum: Hardware
---

### Post by holydogtoffee on 2008-12-09
Hi,

I'm currently installing an Ubuntu system with two Seagate 7200.11 1TB SATA drives.


[B]The pursued system hierarchy would look something like this:
20GB for /
20GB for /home
4096MB for swap
rest (~950GB) for /storage[/B]


Later on, I will add my old Seagate's (320+200GB) to the system and mount them respectively to /storage2 and /storage3 which will not be RAID'ed. So this is not required to do during installation.


Since Ubuntu 8.10 doesn't seem to support setting RAID-partitions in GUI-installation, I have to switch to terminal and use [COLOR="Red"]cfdisk[/COLOR].

How should I partition my hard drive, so that I obtain the wanted system hierachy?
Is it 20GB for a primary using '[COLOR="Red"]Linux raid autodetect[/COLOR]', 4GB for '[COLOR="Red"]Linux swap / Solaris[/COLOR]', rest for logical partition using again '[COLOR="Red"]Linux raid autodetect[/COLOR]'.

Or is the correct way to make a single 1TB primary partition using '[COLOR="Red"]Linux raid autodetect[/COLOR]'?


Both settings would naturally be applied to both sda1 & sdb1.


>>>

After the partition is done, I will move back to console and install mdadm & LVM2 needed for partition.

[COLOR="Red"][FONT="Courier New"]apt-get install lvm2 lvm-common dmsetup mdadm[/FONT][/COLOR]


The next step is a complete mystery for me.

What is needed to do with mdadm & LVM2 in order to achieve the wanted file system hierarchy and get back to the installation part of the OS?

---

### Post by holydogtoffee on 2008-12-10
Bump.

---

### Post by psusi on 2008-12-10
Partition both disks the same way.  Start with the 20 GB raid partition for /, then 4 GB swap partition, then I'd say just partition the rest as raid and mount it as /home and store your files in your documents folder there like normal.

You will want to read the man page for mdadm.  Is there a particular reason you want to use LVM?  If not I would say don't bother.  Also I would suggest using the alternate installer instead of the livecd as it has proper raid support.

---

