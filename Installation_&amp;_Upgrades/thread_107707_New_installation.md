---
title: "New installation"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by jimglennon on 2005-12-23
Sorry for imposing, but I hope someone can 'enlighten' me.  And yes I am very much a beginner with Linux!  I hope you won't hold that against me for a little while yet.

I installed version 5.10 onto a new hard disk drive (the only thing on it might be the Seagate Disk Setup Utility files), restarted the system, and I get this far:

Booting 'Ubuntu, Kernel 2.6.12-9-386
root (hd 0,0)
Filesystem type is ext 2fs, partition type 0 x 83
kernel    /boot/vmlinuz - 2.6.12-9-386
       root=/dev/hdal  ro  quiet splash
[Linux-bzImage.setup = 0 x 1c00, size = 0 x 124blb]
initrd     /boot/initrd.img - 2.6.12-9-386
[Linux - initrd @ 0 x 7b2a000, 0 x 4b56552 bytes]
save default
boot
Uncompressing Linux...ok, booting the kernel.
[4294672.819000] crc error
[4294672.824000] kernel panic - 
        not synching: VFS: unable to mount root fs on unknown- block (0,0)
[4294672.824000]  


I'd appreciate any assistance, I can take bad news as well.  If you need additional info, I'll try to get it.

Thanks in advance.

---

### Post by tay on 2005-12-23
it's unable to mount the partition you decided for it.
because of permissions, the location, or..  who knows.  
sorry thas not much help.

---

### Post by fordfan753 on 2005-12-23
When you say new drive do you mean you just installed it into your computer to put Ubuntu on and haven't used it? If this is the case it might be worth checking out the jumpers on the back of the drive, see if everything is where it should be.

---

### Post by jimglennon on 2005-12-23
I had to install the capacity-limiting jumper before the disk drive was recognized.  Placed it where the manual said, drive was recognized, and proceeded with initial installation.  
Yes it is new, out of the box, installed just for Ubuntu, and hasn't been used for anything else except for the Seagate Disk Utilities program to initially set up the HD.  During the Ubuntu installation, when given the option of erasing the drive (first choice of the four given), I chose that one.

---

### Post by jimglennon on 2005-12-23
OK - one hurdle passed.  I did another re-install, made different selections one or two places during the process and the OS booted and is in the process of installing other programs/packages. 

Thank you folks for the assist.

---

