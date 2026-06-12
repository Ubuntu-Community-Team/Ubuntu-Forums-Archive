---
title: "My friend has a relic"
date: 2008-09-20
forum: General Help
---

### Post by Monotoko on 2008-09-20
Hiya people, my friend was given a computer by his college, they were giving loads of them, hes not very good with computers, so asked me to go and look at it, he told me it had linux installed, but had no idea of anything else.

The first thing i did was boot it up, he hadnt tried it yet, and it gave me a screen, asking for the username, what amazed me was the fact that it was a CLI, intrigued, i tried to get in, couldnt, So i decided to open the computer up, inside i found 4mb of ram, and something with copyright 1982.

It has no CD drive, just a floppy drive, just to give you the scale of how old this thing is.

I was thinking how can i get into it, when i thought about a linux live CD, i was wondering if there were such things as linux live floppys?

It would need to be a CLI though, i dont think it could cope with graphics, does anyone know where i can get a relic OS for a relic machine?

---

### Post by mb_webguy on 2008-09-20
Try [this]("http://rescup.winbuilder.net/bootdisk/").  There's no such thing as a LiveFloppy.  Linux distros can be very small, but never *that* small.  However, this boot disc should be enough to boot the PC and look around the drive.

EDIT: By the way, I can see why the college was giving those PCs away...  Good luck finding any use for it other than as a museum piece.

---

### Post by Monotoko on 2008-09-20
okay, and how do i put the .img on a floppy? (i havent used floppies since 1995 -.-)

do i just stick it on like that? or is there something i have to do?

---

### Post by mb_webguy on 2008-09-20
> **Monotoko said:**
> okay, and how do i put the .img on a floppy? (i havent used floppies since 1995 -.-)

do i just stick it on like that? or is there something i have to do?

Make sure the floppy isn't mounted, then use the command "sudo dd if=floppy.img of=/dev/fd0" to write the image to the disk, replacing fd0 with the actual device id of the floppy drive.

---

### Post by Monotoko on 2008-09-20
how do i find out the device ID? (i only started with linux a few weeks ago, im used to A:/ :P)

---

### Post by linux_tech on 2008-09-20
Hmmm 4 MB RAM- maybe a 286 or 386.  You could try minix--but if it doesn't work , you may need to upgrade RAM to 8 MB.
[http://www.minix3.org/](http://www.minix3.org/)

---

### Post by mb_webguy on 2008-09-20
> **Monotoko said:**
> how do i find out the device ID? (i only started with linux a few weeks ago, im used to A:/ :P)

"sudo fdisk -l" will list all partitions on all drives connected to your system.  "df" will list all mounted partitions on your system, along with their mount points.  A simple comparison of the two should help you identify your floppy drive.  If it's an internal drive, the device id will likely begin with fd, while if it's a USB drive it will likely begin with sd.  And it will be the one that's ridiculously small.

---

### Post by Iowan on 2008-09-20
[LOAF]("http://www.linuxdevices.com/links/LK8414188089.html") (Linux On a Floppy), [tomsrtbt]("http://www.toms.net/rb/") (not a full distro). [picoBSD]("http://people.freebsd.org/~picobsd/") no longer exists. [Freesco]("http://www.freesco.org/") is a router, but a working OS. [Coyote]("http://www.coyotelinux.com/") - another router/micro distro. Most require >4M RAM, though...

3.5" or 5.25" floppies?

More complete list [here]("http://ubuntuforums.org/showthread.php?t=575456").

---

### Post by Monotoko on 2008-09-20
The computer has a 5.25"

I have a USB thing and a 5.25" floppy

---

### Post by Monotoko on 2008-09-20
I have the USB image, as my friend tells me he managed to install a USB port in it, how do i burn that onto a USB drive?
(minix)

---

### Post by Predator106 on 2008-09-20
Heh, wrong terminology, it wouldn't be "burn", more like copy, kinda funny hearing it in this context, but anyways look here...

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Hopefully that helps ya out. Although, you "may" be better off using a USB external if you have one, and if the BIOS supports it, otherwise you will degrade the flash drive. But the problem is, since it sounds like an old computer, it "may" not support booting from USB. At least that's what I heard though, but only one way to find out...

---

### Post by lswb on 2008-09-20
When the computer boots, what processor does the BIOS say it has? If it's a 286 linux and other 32 bit OS won't run on it. If it's a 386 you'll need to compile a custom kernel on another machine or locate one somewhere that you can download. Mainstream standard kernels no longer support a 386 even though they may use "386" in the name.

---

### Post by Monotoko on 2008-09-20
Its 386 -.-

Okay, so how do i compile a custom kernal? this is now into new teritory for me

---

