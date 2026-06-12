---
title: "Ubuntu crash, can no longer access Ubuntu"
date: 2010-02-12
forum: Hardware
---

### Post by Pugnax on 2010-02-12
Forgive me if this is in the wrong forum, I wasn't sure whether to post this in the laptop section, or the install/update section, x86 64 bit section, or the Dell section. Please move if wrong.

Anyway, I've been using Ubuntu for some time, having installed it as a dual-boot on a Dell Inspiron 1501 (with an AMD64 processor), with WinXP. I had recently updated my Ubuntu install (just last night, as a matter of fact). This morning, my computer crashed due to overheating issues --this is a separate problem which I've had to deal with.

At any rate, I booted back up to find myself in the Grub command line. I've googled around and found several solutions, however, none of them work. This has happened before --computer shutting down improperly after an update, or even properly, to find my ubuntu install conspicuously gone, grub not loading properly, etc.

I've tried the following:
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

However, when I try the first poster's solution, the install says there must be a root device, and it gives me no option to do this, nor mount any other devices. 

The second solution does not work, as grub cannot find stage1 file. 


I've toyed around with my FS in the livecd desktop environment, and it seems as though it cannot find the ubuntu partition on the disk. I can only access my windows partition's files. Interestingly enough, my HDD is 55 GB, but my ubuntu's partition is about 20 GB, and the LiveCD desktop environment recognizes that the Windows part is only 16.3 GB. 

"mount | tail -1" reveals:
/dev/sda2 on /media/7080983C80980B2C type fuseblk (rw, nosuid, nodev, allow_other, default_permissions, blksize=4096)

"fdisk -l" reveals:
/dev/sda1 ||    1 ||               9 ||                72261            || de ||       Dell Utility
/dev/sda2 ||   10 ||             6688          || 53649067+ ||       7 ||         HPFS/NTFS
/dev/sda3 ||    6690 ||        7295 ||              4867695 ||       db ||        CP/M  /  CTOS  /  ...

(excuse the awkward formatting)

I initially thought that /dev/sda3 was the ubuntu partition, within are some folders pertaining to dell, such as:

bat/bin/img/src1 and so forth with several .exe .com .bat .bin .sys files. 

I feel as though the LiveCD obviously cannot find the Ubuntu part because whenever I try to run "grub" command, bash mentions that grub is not recognized as a valid command. I have to download and install it. Though when I do, it still cannot find stage1.

I hope I'm being clear. The last time this happened --grub being wiped out after an ubuntu update-- I was forced to reinstall Ubuntu entirely, which overwrote all the important files I had saved. It is important to note that at that time I could not access my ubuntu install either. I'm basically in the same predicament but do not want to resort to the same means.

---

### Post by IcarusR on 2010-02-12
My guess is your partition table is messed up.
Testdisk may be able to help you.

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

Or one of the many utils on 'Hirens Boot CD' google for it.

So if you had to reinstall ubuntu once before & lost data why have you not learnt & done backups ????

---

### Post by Pugnax on 2010-02-12
> **IcarusR said:**
> My guess is your partition table is messed up.
Testdisk may be able to help you.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Or one of the many utils on 'Hirens Boot CD' google for it.

So if you had to reinstall ubuntu once before & lost data why have you not learnt & done backups ????
One would expect such a freak accident to be an isolated incident. Thankfully the only material I lost previously are school files. A better question would be: why hadn't I learned before and moved to a separate distro altogether? Or: why do routine updates without a proper restart cause grub to be erased, or a partition to become corrupt? 

I appreciate your thoughts, and the suggestion of using TestDisk. TestDisk was able to find ext4 data, but by that I could not find the Superblock. On top of that, TestDisk listed some 10 or so different ext4 areas of the partition map. I tried to rewrite the MBR, and booting into Ubuntu, though it still takes me to the Grub command line.

---

