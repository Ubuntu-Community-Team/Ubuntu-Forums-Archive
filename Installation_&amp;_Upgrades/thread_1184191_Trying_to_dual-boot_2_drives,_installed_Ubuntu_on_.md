---
title: "Trying to dual-boot 2 drives, installed Ubuntu on one and now get GRUB error 21"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by rainwalker on 2009-06-10
I have two hard drives, formerly in RAID0 configuration, with Vista installed on one of them. I wanted to install Ubuntu on the other, so I was told to change the boot order so that the blank hard drive was before the one with Vista on it, and then install Ubuntu and GRUB onto that drive. However, my BIOS (Lenovo Thinkpad w700) wouldn't let me move the second hard drive into my boot sequence at all (it would stay stuck under "Excluded from boot sequence") even after I formatted it as fat32, just for kicks. I still couldn't change it in the boot sequence, so I went ahead and installed Ubuntu (Jaunty) onto the drive, along with GRUB and rebooted, hoping that maybe once an OS was on the drive I would be able to move it. However, I STILL couldn't, so I decided to boot up anyway. Instead of booting into Vista or Ubuntu, all I get is GRUB failing with Error 21.
I know both OSes are installed on separate drives, because Gparted shows it. This leads me to believe that I somehow messed up by MBR or something along those lines.

Please, does anyone know how to handle this? I have no experience dual-booting.

---

### Post by gwoodruff on 2009-06-10
You will want to edit /boot/grub/menu.lst and try changing the default lines:

## default grub root device
## e.g. groot=(hd0,0)


You will also have to remove the leading ## in both lines and try hd0 or hd1 which ever has linux.

---

### Post by rainwalker on 2009-06-10
My menu.lst:
> title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		945f733e-698b-4389-8b84-8b0c48e16a0f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=945f733e-698b-4389-8b84-8b0c48e16a0f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		945f733e-698b-4389-8b84-8b0c48e16a0f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=945f733e-698b-4389-8b84-8b0c48e16a0f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		945f733e-698b-4389-8b84-8b0c48e16a0f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


Does that look right to you?

---

### Post by rainwalker on 2009-06-10
Okay, so I'm able to boot into Windows using the Super Grub Disc, but I don't know where to go from there. The Vista install disc finds nothing to repair when I try to.

What do I do from here?

---

### Post by confused57 on 2009-06-10
Here are some possible solutions for grub error 21:
[http://members.iinet.net.au/~herman546/p15.html#21](http://members.iinet.net.au/~herman546/p15.html#21)

You might want to go into your bios setup & make sure the hard drive controller for your Ubuntu drive is set to "auto" or "on".

If this doesn't work, you can restore your Window's IPL to the mbr, using SGD...I think the option is "Fix Boot of Windows".

---

### Post by rainwalker on 2009-06-11
SOLVED: The whole time, the problem was that the hard drive with Ubuntu on it was not in the boot sequence because I was trying to add it wrong. Wow :?

---

