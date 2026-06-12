---
title: "Extend drive rendered Ubuntu unusable"
date: 2009-04-23
forum: Hardware
---

### Post by neresis on 2009-04-23
Hi!

I have made something stupid and used Vista "Extend Drive" to combine two windows drives into one instead of good GParted.

I made backup of data I expected to lose; but I was not expecting to have my Ubuntu partitions unusable.

I had in my extended drive Ubuntu installed in 2 partitions, one for 8.04 and other 9.04 and another partition conteined my /home directory.

Now, after extending, Vista combined the drive with the empty space, but in my extended drive (where Ubuntu lies), it looks like mbr is damaged, because even GParted sees it as unallocated.

How can I recover my Ubuntu?

When I check my HDD, I get following results:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a7e236b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11986    96277270+   7  HPFS/NTFS
/dev/sda2           11987       14593    20940727+   5  Extended
/dev/sda5           14472       14593      979933+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.5G  2.0M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 1.5G  2.0M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   76K  1.5G   1% /dev
tmpfs                 1.5G   76K  1.5G   1% /dev/shm
rootfs                1.5G   36M  1.4G   3% /
/dev/sr0              698M  698M     0 100% /cdrom
/dev/loop0            674M  674M     0 100% /rofs
tmpfs                 1.5G   16K  1.5G   1% /tmp
/dev/sda1              92G   40G   53G  44% /media/Caladan


Thanks in advance.
Oz

---

### Post by nyk on 2009-04-23
Hey Neresis! I actually did basically the same exact thing a few weeks ago (last time I trust Microsoft with important things). A good first step is to boot using a LiveCD, then open up a terminal and run testdisk (I never actually used it from the Live CD so you may need to dl it first...).

Once you've got it running, (and have created a backup), run a scan. It may take a bit, and may not find the partitions you had in place. When it is done, and hasn't yet found everything, run a "Deeper Scan." This takes a while, but will find just about every partition you ever had.

After it is done, you then have the option of viewing, and most importantly, backing up all the files you once thought were unreachable. I would recommend doing this before proceeding.

At this point, you can select your old partition structure, and save it to the MBR, and quit testdisk.

Then, type:

```

sudo grub
> root (hd*,**)
> setup (hd*)
> quit

```

Where * is the number of your harddrive, and ** is the boot partition of your Ubuntu installation.

At this point, you should be able to reboot into Ubuntu. However, this is where I gave up, as I just got the important stuff (my data) off my poor, abused partitions, so I just wiped my hdd, and reinstalled everything fresh.


Best of luck, and let me know if you need any more help.

-- Nyk

---

### Post by neresis on 2009-04-23
Hi Nyk!

Thanks for the reply. My problem is solved and I am writing in my Ubuntu 9.04 installation. :)

I did just as you wrote, except for after using TestDisk and restarting, my HDD looked like one big empty drive under Ubuntu LiveCD.

I switched to Vista install CD, which let me fix C with mbrfix (it is also always in reach).

After that I used once more TestDisk, which showed everything correctly. I did not have to write once more that time. Then I booted once more with Ubuntu live CD and fixed grub.

I lost my 8.04, but it is not even a real loss.

Thanks again.
Cheers!

---

### Post by nyk on 2009-04-23
Glad to help!

---

