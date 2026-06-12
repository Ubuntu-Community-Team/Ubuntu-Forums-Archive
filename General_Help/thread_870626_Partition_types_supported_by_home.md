---
title: "Partition types supported by /home?"
date: 2008-07-26
forum: General Help
---

### Post by GeoMX on 2008-07-26
I'd like to know what type of partitions can I mount /home to?

I have Windows Vista installed on a NTFS partition, also an ext3 with Ubuntu (whole system in one partition), what I'd like is to create another partition and mount /home on it, but also move the Windows Users folder to this partition, so I need a partition that can be accessed by both systems: Vista and Linux (Ubuntu).

Sometime ago I tried mounting /home to a fat (fat32? don't remember) partition and got an error message explaining it was not possible.

In Windows XP it was possible by using an ext3 driver, but I've found that current versions of this kind of drivers do not work in Windows Vista without problems/issues.

Thanks in advance for your help.

---

### Post by ajmorris on 2008-07-26
> **GeoMX said:**
> I'd like to know what type of partitions can I mount /home to?

I have Windows Vista installed on a NTFS partition, also an ext3 with Ubuntu (whole system in one partition), what I'd like is to create another partition and mount /home on it, but also move the Windows Users folder to this partition, so I need a partition that can be accessed by both systems: Vista and Linux (Ubuntu).

Sometime ago I tried mounting /home to a fat (fat32? don't remember) partition and got an error message explaining it was not possible, in Windows XP it'd be possible by using an ext3 driver, but I've found that current versions of this kind of drivers do not work in Windows Vista without problems/issues.

Thanks in advance for your help.

Hi there,
you dont really want a fat home partition. However, you could format it in many different types, it is up to your own personal preference. You can find on the internet, URLs that will help you understand the difference between them :) As for vista being able to access it, you can get tools for windows that allow the mounting, reading and writing to ext, reiser(fs) partition types etc. And if you went with NTFS, you can write to it in linux. I recommend that you use ext3.

AJ

---

### Post by GeoMX on 2008-07-26
I've used a Windows program that allows the reading of ext partitions, but a driver that allowed it to the whole system would be the option.

I'd like to go with an ext3 partition, I've followed a read only discussion in this forum (titled something like "ext3 in Windows Vista") and seems that no driver works perfect for this Windows version.

---

### Post by GeoMX on 2008-08-04
What do you think of using an ext2 partition? I've read this one is fully supported by the driver at [www.fs-driver.org](www.fs-driver.org)

---

### Post by GeoMX on 2008-09-03
I've been using the driver at [http://www.fs-driver.org/](http://www.fs-driver.org/) for some time now: I created an ext3 partition, I mounted /home on this partition and moved my Windows Vista user folders to it too. I've noticed some problems under Windows:
- I'm not able to run almost all executable programs, I get an error message saying: "The parameter is incorrect".
- Visual Studio 2008 crashes when trying to access some converted projects (created with VS 2005).

Does anybody know what other type of partitions can I mount /home to besides ext?

Thank you.

---

### Post by jerome1232 on 2008-09-03
I've always handled that by creating a small /home partion, and a large data partition ntfs mounted at /mnt/data, I symlinked any folder that would contain alot of data in my /home to folders on the data partition.

That way it "feels" like I'm not using multiple partitions while in linux.

---

### Post by 7raTEYdCql on 2008-09-03
I would recommend that you use ext3. ext3 is basically an advanced version of ext2.

---

### Post by GeoMX on 2008-09-06
> **jerome1232 said:**
> I've always handled that by creating a small /home partion, and a large data partition ntfs mounted at /mnt/data, I symlinked any folder that would contain alot of data in my /home to folders on the data partition.

That way it "feels" like I'm not using multiple partitions while in linux.
This one seems as a good option, I'll try it as soon as I can make a backup of my current data, thanks a lot :).
Just one question: what would be the advantage/disadvantage of using a NTFS partition instead of a FAT? I think I will try with FAT, supported natively by both: Windows and Linux.

> **i.mehrzad said:**
> I would recommend that you use ext3. ext3 is basically an advanced version of ext2.
Actually, I have an ext3 partition, but the Ext2-IFS driver for Windows just supports mounting it as an ext2, and I don't think this would be the problem, Windows Vista is likely to check some file signature (or something similar, I'm just guessing here) that only works in a NTFS partition.

---

### Post by GeoMX on 2008-09-07
I switched to the ext2fsd driver (this one is open source), I have no problems with my Visual Studio projects now :), but the executables issue remains :(. I have noticed that only program installers fail, any other executable runs without trouble.

I've been using this driver one day though, and still have to check whether any other issues arise.

---

### Post by GeoMX on 2008-09-13
Bad news, while solving the issue with VS.net projects (I found out that it didn't fail with any C++ projects but only with VB and VC#), the ext2fsd driver brought some instability to my system, it crashed randomly when accessing some folders in my ext3 shared partition.

So I guess I will go with the small ext3 /home partition and the NTFS shared one + symlinks.

---

### Post by mb_webguy on 2008-09-13
That's what I have (a small home partition and a separate shared partition for files), and it works well.  Since I primarily use Ubuntu, I was originally going to have my shared partition formatted as ext3, and use the third-party driver for Windows, but after a little research it seemed that ntfs-3g was more solid on Linux than either of the ext3 drivers are on Windows.

The only real issue with this approach is that NFTS doesn't use Linux-type file permissions, so everything on the partition use the partitions set for the partition by umask in the fstab entry.  But since this is a single-user system, and the NTFS partition is just for file storage, it's rarely a problem.

---

