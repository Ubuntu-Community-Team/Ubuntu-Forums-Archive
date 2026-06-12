---
title: "Grub / not making it past initramfs"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by EtanSivad on 2009-03-26
I've got a bit of an odd setup I'm working on here.  I'm trying to get Ubuntu running on a laptop where I use a USB pendrive to load grub, then boot off of a Compactflash card in the PCMCIA slot.  The laptop boots from USB drives just fine, but there's no Bios Option for booting from the CF card, even though it's an IDE drive to the PC (Nice BIOS Dell!!)
In any event, I'm getting closer.  I've got grub running on the USB drive fine.  It starts to work, but during the boot process it dumps me to the (initramfs) console.  
My menu.lst for booting is:
> title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
chainloader	+1
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cf3f3cb1-3c4c-45b4-8e3e-89af97176ce0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

And when I look up the boot log it's failing on the error:
> ALERT! /dev/dsik/by-uuid/cf3f3cb1-3c4c-45b4-8e3e-89af97176ce0 does not exist. Dropping a shell!

I'm confused by this.  If I run the live CD I can see the disc there under /dev/dsik/by-uuid/cf3f3cb1-3c4c-45b4-8e3e-89af97176ce0 but from the initramfs it's not there.  Any ideas what's happening?

---

### Post by absolutezero1287 on 2009-03-26
> **EtanSivad said:**
> I've got a bit of an odd setup I'm working on here.  I'm trying to get Ubuntu running on a laptop where I use a USB pendrive to load grub, then boot off of a Compactflash card in the PCMCIA slot.  The laptop boots from USB drives just fine, but there's no Bios Option for booting from the CF card, even though it's an IDE drive to the PC (Nice BIOS Dell!!)
In any event, I'm getting closer.  I've got grub running on the USB drive fine.  It starts to work, but during the boot process it dumps me to the (initramfs) console.  
My menu.lst for booting is:


And when I look up the boot log it's failing on the error:


I'm confused by this.  If I run the live CD I can see the disc there under /dev/dsik/by-uuid/cf3f3cb1-3c4c-45b4-8e3e-89af97176ce0 but from the initramfs it's not there.  Any ideas what's happening?

```
sudo blkid
```
Then instead of using /dev/disk/by-uuid/ use UUID=

---

### Post by EtanSivad on 2009-03-26
> **absolutezero1287 said:**
> ```
sudo blkid
```
Then instead of using /dev/disk/by-uuid/ use UUID=

Where?  In the menu.lst?  or in the etc/fstab?  
everywhere I've looked lists purely the UUID=
The only time the /dev/disk/by-uuid comes up is in the error.

---

### Post by absolutezero1287 on 2009-03-26
> **EtanSivad said:**
> Where?  In the menu.lst?  or in the etc/fstab?  
everywhere I've looked lists purely the UUID=
The only time the /dev/disk/by-uuid comes up is in the error.

Do it in the menu.lst.

---

### Post by EtanSivad on 2009-03-26
> **absolutezero1287 said:**
> Do it in the menu.lst.

But my menu.lst already is set to UUID=  :confused:
See:
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=cf3f3cb1-3c4c-45b4-8e3e-89af97176ce0 ro quiet splash

---

### Post by absolutezero1287 on 2009-03-26
> **EtanSivad said:**
> I've got a bit of an odd setup I'm working on here.  I'm trying to get Ubuntu running on a laptop where I use a USB pendrive to load grub, then boot off of a Compactflash card in the PCMCIA slot.  The laptop boots from USB drives just fine, but there's no Bios Option for booting from the CF card, even though it's an IDE drive to the PC (Nice BIOS Dell!!)
In any event, I'm getting closer.  I've got grub running on the USB drive fine.  It starts to work, but during the boot process it dumps me to the (initramfs) console.  
My menu.lst for booting is:


And when I look up the boot log it's failing on the error:


I'm confused by this.  If I run the live CD I can see the disc there under /dev/dsik/by-uuid/cf3f3cb1-3c4c-45b4-8e3e-89af97176ce0 but from the initramfs it's not there.  Any ideas what's happening?

I think I see the problem now. You've got grub loading off of a pendrive but your filesystem is on a flash drive..

This is most interesting.

I would think that you would make a partition in your pendrive where you would mount the /boot directory. You would then modify your fstab to have your other directories mounted under the flash drive.

That way the /boot directory contains the kernel, grub, initramfs and everything needed to boot up. The method I describe should work (in theory) because many people have a separate /boot partition and the system works just fine.

---

### Post by EtanSivad on 2009-03-26
> **absolutezero1287 said:**
> I think I see the problem now. You've got grub loading off of a pendrive but your filesystem is on a flash drive..

This is most interesting.

I would think that you would make a partition in your pendrive where you would mount the /boot directory. You would then modify your fstab to have your other directories mounted under the flash drive.

That way the /boot directory contains the kernel, grub, initramfs and everything needed to boot up. The method I describe should work (in theory) because many people have a separate /boot partition and the system works just fine.

Ok, you've got it now.  It's basically -> Boot from USB drive -> Load filesystem off of Compact flash drive.

I've got the initrd and the kernel on the pen drive, but for some reason initrd just doesn't want to mount the flash drive.  The kernel mounts it fine.  Everything is spelled out in the fstab.

---

### Post by absolutezero1287 on 2009-03-26
> **EtanSivad said:**
> Ok, you've got it now.  It's basically -> Boot from USB drive -> Load filesystem off of Compact flash drive.

I've got the initrd and the kernel on the pen drive, but for some reason initrd just doesn't want to mount the flash drive.  The kernel mounts it fine.  Everything is spelled out in the fstab.

There is a way with all Linux distros to boot directly into the kernel and not use an initramfs or ramdisk. Comment out the line pointing grub to the initramfs by placing a "#" in front it.

```

title           Ubuntu 8.04.2, kernel 2.6.24-24-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-24-generic root=UUID=266f6e91-8868-40e7-8403-db497e32fe28 ro quiet splash
initrd          /boot/initrd.img-2.6.24-24-generic

```

```

title           Ubuntu 8.04.2, kernel 2.6.24-24-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-24-generic root=UUID=266f6e91-8868-40e7-8403-db497e32fe28 ro quiet splash
#initrd          /boot/initrd.img-2.6.24-24-generic
#GRUB will skip over anything that's commented out

```

On a sidenote: I've never tried this before but what's the worse that could happen? Ubuntu won't boot and you just use the LiveCD to uncomment that one line.

---

### Post by EtanSivad on 2009-03-27
> **absolutezero1287 said:**
> There is a way with all Linux distros to boot directly into the kernel and not use an initramfs or ramdisk. Comment out the line pointing grub to the initramfs by placing a "#" in front it.

```

title           Ubuntu 8.04.2, kernel 2.6.24-24-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-24-generic root=UUID=266f6e91-8868-40e7-8403-db497e32fe28 ro quiet splash
initrd          /boot/initrd.img-2.6.24-24-generic

```

```

title           Ubuntu 8.04.2, kernel 2.6.24-24-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-24-generic root=UUID=266f6e91-8868-40e7-8403-db497e32fe28 ro quiet splash
#initrd          /boot/initrd.img-2.6.24-24-generic
#GRUB will skip over anything that's commented out

```

On a sidenote: I've never tried this before but what's the worse that could happen? Ubuntu won't boot and you just use the LiveCD to uncomment that one line.

intresting Idea, but I think it needs the initrd to get to the point that it can start loding it up.  I went into the grub menu and deleted the initrd line.
It starts to boot, but fails with a kernel panic that reads:

> VFS: Cannot open root device "UUID=266f6e91-8868-40e7-8403-db497e32fe28" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I get much further with initrd in there, but I think I'm going to research that error message and see what I can find.

---

