---
title: "GRUB: /dev/md1 does not have a BIOS disk"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by jwatte on 2009-09-01
I'm having GRUB problems, where I get one of two errors:
"/dev/md1 does not have BIOS disk"
or
"File system type unknown, partition type 0x83"

I have a Linux system which has been upgraded since 1995 or so (starting on a Pentium-120, now running on a C2D E6550).
The main role of this machine is as file server for backups, music and video. Thus, it's accreted a number of disks over the years, most of which are PATA.

I'm running 8.04 server LTS in x64 mode.

Wise from previous disk failures, I run almost everything as raid1 using md these days. Thus, the disks are something like as follows:

Disk A: (PATA)
 Partition 1: 200 MB, /dev/md1, /boot, reiserfs
 Partition 2: 1500 MB, swap
 Partition 3: 1000 MB, /dev/md2, /, reiserfs
 Partition 4: The rest, /dev/md0, LVM PV
Disk B: (PATA)
  Partition 1: Everything, /dev/md3, LVM PV
Disc C: (PATA)
 Partition 1: 200 MB, /dev/md1, /boot, reiserfs
 Partition 2: 1500 MB, swap
 Partition 3: 1000 MB, /dev/md2, /, reiserfs
 Partition 4: The rest, /dev/md0, LVM PV
Disk D: (PATA)
 Partition 1: Everything, /dev/md3, LVM PV
Disk E: (SATA)
 Partition 1: Everything, LVM PV (video)
Disk F: (SATA)
 Partition 1: Everything, LVM PV (video)

As you can see, I do not raid-1 my video storage, but everything else, including my boot and root partitions. Yay me!
The PATA disks run off the motherboard PATA, and off a separate PCI SiS PATA board, for legacy reasons. (Yes, running everything SATA would be much better -- but that costs money)

Yesterday, I lost disk A to a bad block somewhere in /dev/md2. The annoying part was that the machine would be unusable, even though I was using raid1, because "md" would not recognize that the disk was bad and fail it. I couldn't even log in on the console.

After booting using the installer disk, and using system rescue (in text mode, for compatibility reasons), I finally figured out which disk was bad (I couldn't even log into the machine when it was wedged), and after another while, I figured out how to make the installer environment not try to rebuild my md2, which in turn would cause the disk to hang on the bad block -- I simply wrote an empty partition table to Disk A (which had the bad block), and rebooted -- now md1/md2/md0 run in degraded mode, but at least I can use the machine when booting from the rescue CD.

Disk A was my boot disk, with the master boot record and all that, so despite being mostly RAID, it was a single point of failure.

All I need to do now is re-install GRUB to point it at disk C instead of disk A, right? Then find a replacement disk A
Well, I tried that, and got the "/dev/md1 does not have BIOS disk" error from GRUB. (I ran the "re-install GRUB" command from the system rescue menu, but had to look in syslog to see the error).

I then created a copy of the files from my /boot onto a fresh partition /dev/sda1, changed my fstab to not mount /dev/md1, but instead mount /dev/sda1, set up all the mounts in the rescue shell environment to match, and then I re-ran the GRUB installer.

At that point, GRUB still fails, but with a dump of some scripted text from grub-installer into syslog. The main error seems to be "File system type unknown, partition type 0x83"

Previously, GRUB has been able to boot into my reiserfs just fine, so what's wrong this time?

Also, I've tried specifying both (hd0) and (hd2) as the boot disk, as well as /dev/sda and /dev/sdc, all with the same annoying outcome.
Now, it may be that GRUB thinks that "sda" is actually BIOS drive 0, and when my BIOS lists the drives, it thinks Drive E is the first drive -- but if so, then the actual /dev/sda device would be (hd2), right? ('cause that's the order it's shown in the BIOS).
Still no dice.

In desperation, I tried installing LILO, but it complains that /boot/boot.b is missing, which it is. Where might I find that file, if I have to go down that route?

---

### Post by jwatte on 2009-09-01
I got the system booting. Here's what I did:

-1) Edit the "boot disk order" in the BIOS to match the /dev/sdX order that Linux sees.

0) Boot the installer in rescue mode

1) Create a small partition on Disk A (/dev/sda1) that is not large enough to hit the bad blocks.

2) Format that partition with mke2fs instead of mkreiserfs

3) Copy the kernel/initrd from my original boot partition

4) Mount everything the way I want it; /dev/sda1 on /boot; update fstab

5) run Grub manually with the following two commands:

root (hd0,0)
setup (hd0)

After that, it didn't give an error, and the system could boot again -- although I'm running in degraded mode, seeing as Disk A is mostly toast (except for the boot partition).

---

