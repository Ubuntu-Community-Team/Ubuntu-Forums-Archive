---
title: "ext3 HDD/partition mount issue, data verification"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by pilpi on 2006-08-27
Hi,

I got a new seagate hard drive in a Delock usb2 3.5" HDD external box. Got it formatted as one huge ext3 (it's going to be a backup drive). 

First of all, there's this problem that when I turn it on simultaneously with the PC, it only sometimes mounts according to fstab. Other times the mounting fails , it throws me into a root console and instructs me to try "e2fsck -b 8193 <device>". Even after this failure if I just say exit in the root console, the drive actually is by the time I get logged in, mounted. Any ideas why this happens and how I can fix it? My fstab entry:
/dev/sda1       /media/bax      ext3    defaults        0       1
Actually I'm just realized that the last param should be 2, but can't make that change right now. I guess that doesn't have to do with the problem, though?

Second, I copied all my files from a FAT filesystem to the new ext3 partition. Now, the "cp -rv /media/omat/* ." command didn't report any problems, but is there a way to verify that the copy process indeed was 100% successful, somehow comparing the data in the old directory and the new one? find * | wc gives the same number of files on each, but du gives a bit different sizes for the two directories (due to block size or something?).

Thanks for any help.

---

### Post by aurelieng on 2006-08-27
First, the last parameter on the line in fstab should be zero, so that the disk is never checked at boot. Otherwise, each time it is not mounted, you'll face a prompt.

Second, you can for instance use "diff -r" (-r = recursive diff, man diff) or rsync (man rsync) to ensure that all your files are correctly copied.

---

### Post by pilpi on 2006-08-30
Seems that disabling the check  is just ignoring the issue, not fixing it. I guess something must be wrong if the partition only sometimes mounts at boot?

Thanks for the verification tip, must try them.

---

### Post by pilpi on 2006-09-04
I finally copied the files with rsync, trusting that it verifies stuff sufficiently though it's hard to know.

The mounting problem still remains. Any help?

---

### Post by pilpi on 2006-09-09
Hi. Decided to grab a screenshot of the problematic situation. This is with the fstab line 

/dev/sda1       /media/bax      ext3    defaults        0       1

If I set the last parameter to zero, this error doesn't happen. But I'm afraid that if I set it to zero, some essential checks will not get made and then things will become messy because of that?

In all cases, the hard drive is anyway monted by the time I get to my desktop.

Is it just that it tries to mount it before USB support is loaded, or what? If so, how to fix it? I'm afraid of continuing to create my backup system on this hard drive before I know it's alright.

Please, please help.

---

### Post by pilpi on 2007-01-20
this issue is still open. any help?

---

