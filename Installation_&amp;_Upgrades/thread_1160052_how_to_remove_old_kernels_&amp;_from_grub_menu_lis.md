---
title: "how to remove old kernels &amp; from grub menu list &amp; disc left"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by metaxa1 on 2009-05-15
Hello,
I have tried various ways to remove old kernels - via Synaptic manager, removing linux-images but still when I start my laptop in grub i have all kernels that I had installed.

My goal is to remove all old kernels (pshicyl from disk, and from boot loader) I want to keep only **2.6.27-14-generic & Windows XP **

My previous kernels are not working, so I don't see reasons for keeping them, and I had made backup.

Also from previous kernel i have 22,0 gb media partition left, in which I can see there are linux files from that kernel that I don't want to use. How to safe delete it, and add that space to some other partition, maybe even to NTFS?

Thanx in advance


This is c/p from my menu.lst 

> title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		39f8fa3e-f0c1-46ff-9622-9c3877b10df0
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=39f8fa3e-f0c1-46ff-9622-9c3877b10df0 ro splash vga=792 quiet 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		39f8fa3e-f0c1-46ff-9622-9c3877b10df0
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=39f8fa3e-f0c1-46ff-9622-9c3877b10df0 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		39f8fa3e-f0c1-46ff-9622-9c3877b10df0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=39f8fa3e-f0c1-46ff-9622-9c3877b10df0 ro splash vga=792 quiet 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		39f8fa3e-f0c1-46ff-9622-9c3877b10df0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=39f8fa3e-f0c1-46ff-9622-9c3877b10df0 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		39f8fa3e-f0c1-46ff-9622-9c3877b10df0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cfcfadc4-6931-47d8-a478-f95c1d989cec ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cfcfadc4-6931-47d8-a478-f95c1d989cec ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 9.04, kernel 2.6.27-11-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cfcfadc4-6931-47d8-a478-f95c1d989cec ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cfcfadc4-6931-47d8-a478-f95c1d989cec ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 9.04, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


---

### Post by spcwingo on 2009-05-15
The easiest way is to install Ubuntu-Tweak.  It gives you a nice little GUI to do this and a whole lot more.  More information here:

[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

If that's a no-go, then you have to manually edit your /boot/grub/menu.lst after uninstalling the old kernels.

---

### Post by metaxa1 on 2009-05-15
> **spcwingo said:**
> The easiest way is to install Ubuntu-Tweak.  It gives you a nice little GUI to do this and a whole lot more.  More information here:

[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

If that's a no-go, then you have to manually edit your /boot/grub/menu.lst after uninstalling the old kernels.

I did that, but i only got rid off 
Ubuntu 8.10, kernel 2.6.27-7-generic
title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
title Ubuntu 8.10, memtest86+

The others are still there, so i is the disk.

---

### Post by spcwingo on 2009-05-15
Well, from what I understand, Jaunty uses a different version of GRUB, so I recommend that you wait for someone else with more experience working with that version (I'm still on Hardy) so we don't end up bricking your install.  ;)

---

### Post by metaxa1 on 2009-05-16
OK, anyone else with the help tips?

---

### Post by martin_lindhe on 2009-12-19
> **metaxa1 said:**
> OK, anyone else with the help tips?

i know this is late, but i saw the thread just now

the easiest way to get rid of old kernels from grub is to uninstall the package, the post-install scripts will update grub

for example my current kernel is:

  uname -a
  Linux hemma 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

then remove older kernels found in /boot like this:

  sudo aptitude remove linux-image-2.6.31-15-generic linux-image-2.6.31-14-generic linux-image-2.6.31-13-generic

---

### Post by shokoup on 2010-11-11
> **spcwingo said:**
> The easiest way is to install Ubuntu-Tweak.  It gives you a nice little GUI to do this and a whole lot more.  More information here:

[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

If that's a no-go, then you have to manually edit your /boot/grub/menu.lst after uninstalling the old kernels.

:guitar:  really easiest way to use tweak

---

### Post by Bunghi on 2011-01-13
After removing old kernels with Ubuntu-Tweak just type in a terminal:

```
sudo update-grub2
```

---

