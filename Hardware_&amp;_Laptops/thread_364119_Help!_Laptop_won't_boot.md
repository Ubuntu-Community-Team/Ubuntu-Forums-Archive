---
title: "Help! Laptop won't boot"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by figgles on 2007-02-17
I've been running ubuntu for at least 6 months now and love it. However, while running xtightvncviewer, my laptop locked up and I couldn't force a a gdm restart. So I cut the laptop off and rebooted. However, the laptop will no longer boot. During the boot process, I'll see:

kjounald starting. Commit interval 5 seconds
Done.
run-init: /sbin/init: I/O error
Kernel panic - not syncing! Attempted to kill init!

at which point the cpu fan will start to roar and that's about it.

I have tried loading grub (I was in recovery boot mode to see the above) going back to the earliest kernel I had 2.6.15-23-386, whereas I'm normally running 2.6.15-26-686

HELP! (and T.I.A.)

---

### Post by DagMan on 2007-02-18
I'm thinking the way to try to recover is to boot into a live cd and if your data on your drive isn't corrupted beyond repair, to mount your drives, chroot, and reinstall grub and your kernels.

I don't know if or how to run filesystem recovery tools from a live cd so maybe someone could add that if it's possible.  look at 'man fsck' and 'man e2fsck' though.

To chroot, boot a live cd, mount your drives at /mnt so for example let's assume you have / and /home (we don't worry about swap here) in your install.
You mount / first becuase /home is a subdirectory.
sudo mount /dev/drive&partition#for-root /mnt
sudo mount /dev/drive&partition#for-home /mnt/home

and so on until all your partitons related to your install are mounted.  If it says you must specify a file type then it would be (using ext3 as an example)
sudo mount -t ext3 /dev/drive&partition#for-root /mnt
and so on untill everything is mounted.

I usually do this as root like this
```
sudo su
```

then to run the installed and mounted system from the live cd:
```
mount -t proc none /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt /bin/bash
```

And I think that's all ubuntu requires.
If that goes fine then try, from this command line, to apt-get grub and a kernel image to boot back into your system.

Good luck.  Also, if you don't know where all your partitions are supposed to be mounted and you can get just / mounted then you can have a look at your fstab file 'cat /mnt/etc/fstab'  
Also if that was a bit confusing about how to mount your partitions, post here details like how many hard drives you have on your computer, which partition is your root filesystem, preferably also which partitions your other filesystems are on.  If your drives are refered to as hda or sda would be important too.

---

### Post by figgles on 2007-02-18
FWIW, I tried using a Knoepix live 5.1 disk to run fsck from. fsck returned without errors, so this might be more severe, and yea, that happens on any platform. I also ran Spinrite, which also returned no errors on the low-level end of the spectrum. I am going to try your suggestion before a reinstall but I am deeply grateful for your help!

I've just completed, and am now downloading, a full desktop 6.10 CD. The good news is that ubuntu is a fantastic linux distro, so there's no need to beat my chest about "leaving for Fedora" or what have you. The down side is that, if this were my Mac, I'd have more options for repair, than appears to be the case with ubuntu. For example, I would boot into "single user" mode, run repair utilities from there (as I have in comparable cases) which tend to fix such matters. (It's my guess that the disk journal needs to be resynced) I'm hoping to find a comparable reference for booting into a stripped down OS session in ubuntu; we'll see. My guess is a complete wipe and reinstall. Since open source licensing isn't anything like it is on Mac or Windows, the worst part of a reinstall, re-establishing licensing agreements, for a myriad of applications, is non-existent, at least for me.

---

