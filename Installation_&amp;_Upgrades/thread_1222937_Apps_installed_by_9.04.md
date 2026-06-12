---
title: "Apps installed by 9.04"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2009-07-25
Is there a list of the apps installed by 9.04?

I was surprised that GParted was not installed, is there another partition manager installed? I did not notice any in the Systems menu.

---

### Post by wojox on 2009-07-25
Check here:

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

---

### Post by Howard Kaikow on 2009-07-25
> **wojox said:**
> Check here:

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

Thanx.

Did not know about the ubuntuguide site.

---

### Post by Howard Kaikow on 2009-07-26
I found the URL I had seen 2+ years ago.

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by presence1960 on 2009-07-27
> **Howard Kaikow said:**
> I found the URL I had seen 2+ years ago.

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

gparted is not installed by default on Ubuntu. Open a terminal and run ```
sudo apt-get install gparted
```

---

### Post by Howard Kaikow on 2009-07-27
> **presence1960 said:**
> gparted is not installed by default on Ubuntu. Open a terminal and run ```
sudo apt-get install gparted
```

Ayup, I did that.

It seems strange to install an OS without a default partition manager.

---

### Post by iNaitvad on 2009-07-27
agree, in the installer there is Gparted, but after install its gone.
I installed a Ubuntu System with a XFS partition, the installer let me choose XFS, but i couldnt use it after install, so i installed xfs-progs, you should try installing ntfs-progs, also...

---

### Post by oldfred on 2009-07-27
I think the assumption is that you do not need the partition manager in the working copy of ubuntu. You cannot edit partitions on mounted drives, so you normally use the CD to edit partitions. Only if you are an advanced user and have many partitions or multiple hard drives would you want to install gparted.

---

### Post by Howard Kaikow on 2009-07-27
> **iNaitvad said:**
> agree, in the installer there is Gparted, but after install its gone.
I installed a Ubuntu System with a XFS partition, the installer let me choose XFS, but i couldnt use it after install, so i installed xfs-progs, you should try installing ntfs-progs, also...

I have yet to summon the courage to write to my Windows NTFS partitions via Linux. I might find such courage if NTFS were supported by the kernal.

I maintain a single FAT32 for communicating 'tween Linux/Windows.

---

### Post by Howard Kaikow on 2009-07-27
> **oldfred said:**
> I think the assumption is that you do not need the partition manager in the working copy of ubuntu. You cannot edit partitions on mounted drives, so you normally use the CD to edit partitions. Only if you are an advanced user and have many partitions or multiple hard drives would you want to install gparted.

I have 4 SCSI drives with 11 Windows partitions, 4 of which are OS, and 4 Ubuntu partitions (swap, /, /home, and /opt).

However, due to the crappy Partition Manager I have in Windows, it does not play nice with partitions created by GParted. I had to pre-partiion before theUbunntu install using Partition Magic.

Neither Windows nor, e.g., Perfect Disk have any problems with GParted created partitions, it's a Partition Magic feature/bug.

And, I cannot use the GParted CD on either my desktop (old Pentium iI), or notebook (a bit over 1 year old). I've reported this in the GParted forum. I can use GParted from an Ubuntu Live CD or from the Parted Magic CD, so I guess there are some missing video drivers  for the GParted Live CD.

---

