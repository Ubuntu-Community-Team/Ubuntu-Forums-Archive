---
title: "Dual-Boot w/ External HDD"
date: 2009-09-25
forum: Hardware
---

### Post by txwooley on 2009-09-25
I am trying to dual-boot two Ubuntu OS's.  I have 8.04 on my laptop HDD working with no problems.  I installed 8.10 onto a Seagate Freeagent Xtreme 1.5TB external HDD connected via firewire.  I have been able to resolve most issues around the GRUB errors and Seagate falling asleep at the wheel, and 8.10 appears to be successfully installed on the external HDD (when viewing it in file browser on 8.04).  My problem lies in my computer (or GRUB) not seeing the 8.10 OS when I boot.  This is not a BIOS problem, because I had 8.10 installed on a 8GB flash drive and working great before I gave the flash to my wife and bought myself this external HDD. fdisk -l shows both HDD's to be mounted and both have boot sectors:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00052874

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd160521c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      181314  1456404673+  83  Linux
/dev/sdb2          181315      182401     8731327+   5  Extended
/dev/sdb5          181315      182401     8731296   82  Linux swap / Solaris

```

When I start the computer and pres ESC while GRUB is loading, it lists all the old kernel versions of 8.04 but does not list 8.10 at all.  I edited 8.04's /boot/grub/menu.lst to reflect something similar to the menu.lst created for 8.10 by adding to the end of the file:

```
## ## End Default Options ##

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=6a7ed977-d63b-4333-81d8-ce0f088014b3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=6a7ed977-d63b-4333-81d8-ce0f088014b3 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=6a7ed977-d63b-4333-81d8-ce0f088014b3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=6a7ed977-d63b-4333-81d8-ce0f088014b3 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=6a7ed977-d63b-4333-81d8-ce0f088014b3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=6a7ed977-d63b-4333-81d8-ce0f088014b3 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=6a7ed977-d63b-4333-81d8-ce0f088014b3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=6a7ed977-d63b-4333-81d8-ce0f088014b3 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6a7ed977-d63b-4333-81d8-ce0f088014b3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6a7ed977-d63b-4333-81d8-ce0f088014b3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6a7ed977-d63b-4333-81d8-ce0f088014b3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6a7ed977-d63b-4333-81d8-ce0f088014b3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


splashimage=3d3ef3af-a5a6-46cf-a08e-6376ffb64e3a/boot/grub/splash.xpm.gz

title		Ubuntu 8.10, kernel 2.6.29.4
uuid		3d3ef3af-a5a6-46cf-a08e-6376ffb64e3a
kernel		/boot/vmlinuz-2.6.29.4 root=UUID=3d3ef3af-a5a6-46cf-a08e-6376ffb64e3a ro quiet splash 
initrd		/boot/initrd.img-2.6.29.4
quiet

title		Ubuntu 8.10, kernel 2.6.29.4 (recovery mode)
uuid		3d3ef3af-a5a6-46cf-a08e-6376ffb64e3a
kernel		/boot/vmlinuz-2.6.29.4 root=UUID=3d3ef3af-a5a6-46cf-a08e-6376ffb64e3a ro  single
initrd		/boot/initrd.img-2.6.29.4

title		Ubuntu 8.10, memtest86+
uuid		3d3ef3af-a5a6-46cf-a08e-6376ffb64e3a
kernel		/boot/memtest86+.bin
quiet
```

Everything after "### END DEBIAN AUTOMAGIC KERNELS LIST" I added.  Now when I boot, it still goes directly into 8.04 unless I press ESC where I do get the options for 8.10 and it's recovery mode as well as the memtest.  When I select 8.10 I get "ERROR 17 FILE NOT FOUND".  Please help me make this stupid thing boot 8.10 from the HDD.

---

### Post by swoody on 2009-09-25
In the sections that you added, try changing them to this:

```
title		Ubuntu 8.10, kernel 2.6.29.4
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.29.4 root=/dev/sdb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.29.4
quiet

title		Ubuntu 8.10, kernel 2.6.29.4 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.29.4 root=/dev/sdb1 ro  single
initrd		/boot/initrd.img-2.6.29.4

title		Ubuntu 8.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
```

Then save it, and reboot, and see if you still get the same error.

Also, when you installed Ubuntu 8.10, did you install Grub onto the the external drive? There may be a better way around this, as the Grub entries on your laptop won't update when you upgrade to a new kernel in 8.10. So you'll have to manually edit this file every time you change kernels. What I would recommend doing would be to use a live CD, install Grub onto the root partition of the external drive, and then we can set this up as a chain, where this Grub would point to that partition, and the Grub on that partition would then be responsible for booting Ubuntu 8.10 from that drive. This way, any updates you do in the future would be automagically updated when you upgrade kernels in the future.

---

### Post by txwooley on 2009-09-26
I think that did the trick.  I did install root on the external HDD as I kept getting a error code 21 grub not found if I left it on the main HDD and didn't have the external plugged in.  Thanks for the help. Give yourself a bean lol.

---

### Post by swoody on 2009-09-28
Well I'm glad that worked out for you. However, as I mentioned, that will not update your Grub menu when you install new kernels in 8.10. So, I have found an easier way of going about this, and being able to keep your Grub menu(s) up to date. First, let's make a backup of your current menu.lst since we know that it works the way it is. So from a terminal run:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

Now, lets edit your menu.lst:

```
gksu gedit /boot/grub/menu.lst
```

Now delete the entire section of all entries for 8.10, and replace it with:

```
title        Ubuntu (External)
configfile   (hd1,0)/boot/grub/menu.lst
```

This will tell Grub on your internal HDD, that if it wants to boot up Ubuntu 8.10, that it needs to go to the menu.lst on the Grub of your external drive. If you did install Grub to the external drive like you say you did, this should work out a bit cleaner and easier than what I had mentioned above. To edit your Grub menu for your external HDD, you would just have to boot into 8.10, and then you can edit that Grub menu in whatever ways you'd like. That way, you can still setup your default option, and have your recovery and memtest options available.

However, if this has been a terrible failure, you can restore the backup made earlier with:

```
sudo cp /boot/grub/menu.lst-backup /boot/grub/menu.lst
```

And then we can take another shot at getting your boot-loaders chained :)

---

