---
title: "&quot;Grub Disk Error&quot;, otherwise fine...."
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by lazulilasher on 2008-12-14
Greetings:

Well, I just installed Ubuntu onto my old Toshiba Qosmio E15. I chose to install Ubuntu over the entire hard disk.

Everything works fine, except I can only boot via the LiveCD and choosing the "Boot from Hard Disk" option. Then, Ubuntu boots 

If I don't have the LiveCD in the drive at bootup, then I receive a message that says "Grub Disk Error". The system then freezes.

I am not particularly linux-savvy; but, I am curious how I can fix this problem. It would be nice to boot into the OS without having to use the LiveCD. Like I said, once the LiveCD is in the drive, I can boot easily into my Ubuntu installation.

Any ideas?

Thanks in advance!
Laz

---

### Post by Herman on 2008-12-14
Check to make sure your hard disk is plugged in and jumpered correctly and is properly set up in your BIOS. Link: [GRUB hard disk error]("http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_hard_disk_error").

Regards, Herman :)

---

### Post by lazulilasher on 2008-12-14
Hmm...I'll check into that.

While I work on that, I thought I'd attach the output of sudo fdisk -lu.

Here it is:

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4f4670b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149838254    74919096   83  Linux
/dev/sda2       149838255   156296384     3229065    5  Extended
/dev/sda5       149838318   156296384     3229033+  82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   625121279   312560608+   c  W95 FAT32 (LBA)


Maybe that will help :)

Thanks again!

---

### Post by lazulilasher on 2008-12-14
I fixed it! (well, I found a thread of someone who had fixed the problem).

Here it is for anyone that has the same problem in the future:
(first, sudo grub), then:

> 
root (hd0,0)
install --stage2=/boot/grub/stage2 /boot/grub/stage1 d (hd0) /boot/grub/stage2 p (hd0,0)/boot/grub/menu.lst

The thread is: [http://ubuntuforums.org/showthread.php?t=363355&page=4]("http://ubuntuforums.org/showthread.php?t=363355&page=4")

I still am not clear, exactly, what the error was. If anyone could explain it to me in laymen's terms, I would be deeply indebted.

Anyway, thanks much! It all works now, it's great to be back on Linux after a few months of windoze...

---

### Post by Herman on 2008-12-15
> I fixed it! (well, I found a thread of someone who had fixed the problem).Well done, bravo! Very good!
> I still am not clear, exactly, what the error was. If anyone could explain it to me in laymen's terms,
:) I'll give it a try.

As you might already know, a hard disk's MBR is too small to fit an entire boot loader in, so all boot loaders come in two or three 'stages'. 
The stage1 in the MBR is very small, and its only job is to boot stage2 of the boot loader which is (usually) located in a file system inside a partition.
Certain other boot loaders relay the boot from the MBR to a 'boot sector', (the first sector of a partition), from there the boot sector points to a boot loader, which then boots the operating system.
The Linux boot loaders, GRUB and LiLo, are not tied to any partition's boot sector, but you can install a stage1 file for them there if you want to.

When GRUB is installed to a hard disk's MBR, it is normally installed with three stages. 
Stage1 is very small, stage1_5 is much larger and stage2 is very large.
Stage1 goes in the first part of the MBR, stage1_5 is installed in the next fifteen sectors of the otherwise empty first track of the hard disk.
Stage 1 loads stage1_5, which is used because it can understand file systems and it loads stage2, however, the stage1_5 is optional, we can install GRUB without it if we really want to.
Stage2 is in the operating system's file system(s), in the /boot directory. 
 
What it looks like they are saying is, there seems to be a problem with stage1_5 in some hard disks, or maybe only with certain computer's BIOSes, and/or maybe only with some Linux distros and not others. (I suppose when someone is sure exactly what the problem is then it might be possible to fix it, if it's really GRUB's fault). 
Whatever the exact issue is, the workaround for the time being if you do happen to have this (relatively rare) problem is to re-install GRUB with that special install command they advised, and not the usual '[setup]("http://www.gnu.org/software/grub/manual/grub.html#setup")' command.
That install command is listed in the GNU-GRUB Manual, here: [install]("http://www.gnu.org/software/grub/manual/grub.html#install").

That command installs only stage1 to MBR and makes it point directly to the stage2 GRUB file, (without using any stage1_5 at all).
We don't necessarily need GRUB's stage1_5 file. Normally it's better to have it, but if there's a problem with it then it's better to do without it.

Regards, Herman :)

---

