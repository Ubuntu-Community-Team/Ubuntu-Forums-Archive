---
title: "Help, trying to Boot from USB Hard Drive"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by spiffo on 2009-11-08
OK, I'm a bit of a noobie so go easy with me.

I'm a bit short of Internal Hard Drive space on my Dell D420 Laptop so I bought a 2.5" USB Hard Drive and thought I would run Ubuntu from this external drive.

I followed this procedure [http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/)

But my problem is that I can't seem to Boot from the USB Hard Drive alone, I have to have the Ubuntu CD in the drive, the CD is accessed briefly, something about GRUB (the boot loader ?) comes up then it boots normally from the USB Hard Drive. If I try to boot from the USB Hard Drive alone, it just comes up No Bootable Devices, press F1 to try again.

Oh by the way, Booting from USB is an option in the BIOS and I installed USBTest.zip (from pendrivelinux.com) to a spare USB Flash Drive as a test of USB Booting capability and it worked fine so I'm pretty sure it's not a fundamental Hardware problem.

Can anyone help ?

---

### Post by Cr0n_J0b on 2009-11-08
I messed around with this a little bit ago.  Here is what I would do.  I'm not an expert...

take out the internal drive on the laptop.  I wouldn't want grub to mess with that disk.

Set the bios to boot from the CD first then from the USB drive.  I'm assuming that it can do that.

Then put the live CD in and boot from it.  You might be able to go straight to the install part from the CD, but I would boot to the live CD to make sure that your USB drive shows up.

The USB drive should be something like /dev/sda or something.

now select he install button and when the partitioner comes up...hopefully that device will be shown as an optional place to partition and install to.

Partition it (THIS WILL LOSE ALL DATA ON THAT DRIVE!!), format it and click next.

In the next screen there will be an advanced button.  click that and make sure that grub is loaded to your USB drive.  now you can try to complete the installation.  It should work...though I've never done this before.

When you are done you should be able to boot to the USB drive and everything should work.  

Next you need to setup dual boot...here is where my help ends.  I know that you can setup dual boot on either the windows partition or the linux partition, so you need to figure out which you will use most and setup the bootloader for that device to choose from either the linux install or the windows install.

---

### Post by spiffo on 2009-11-08
Yeah, I did all that, and I clicked on the 'Advanced' button, 'Install Boot Loader' and I pointed it at dev/sda

It still hasn't worked though, something went wrong, I still cannot boot from the USB Drive without the CD in as well !

---

### Post by slooksterpsv on 2009-11-08
If you can get into the OS on the External via the CD, get in there and reinstall grub with grub-install.

Depending on your drive, it could be sda0 sdb0 - mine is sda5 (as its a partitioned drive) - type in:
$ sudo grub-install hd0

Where hd0 is the mount of your hdd.

---

### Post by spiffo on 2009-11-09
graham@graham-laptop:~$ sudo fdisk -l
[sudo] password for graham: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x621e27d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29841   239697801   83  Linux
/dev/sda2           29842       30401     4498200    5  Extended
/dev/sda5           29842       30401     4498168+  82  Linux swap / Solaris
graham@graham-laptop:~$ sudo grub-install sda1
[sudo] password for graham: 
grub-probe: error: Cannot stat `sda1'
Invalid device `sda1'.
Try ``grub-setup --help'' for more information.
graham@graham-laptop:~$ sudo grub-install sda
grub-probe: error: Cannot stat `sda'
Invalid device `sda'.
Try ``grub-setup --help'' for more information.


OK, I ran fdisk to find out the partiton and drive arrangement then tried to install grub, firstly onto sda1 and then sda, no joy !

---

### Post by slooksterpsv on 2009-11-11
Try: 
```

sudo grub-install /dev/sda

```

Or grub-setup:
```

===MAN PAGE===
NAME
       grub-setup - manual page for grub-setup (GRUB) 1.97~beta4

SYNOPSIS
       grub-setup [OPTION]... DEVICE

DESCRIPTION
       Set  up images to boot from DEVICE.  DEVICE must be a GRUB device (e.g.
       ``(hd0,1)'').

       -b, --boot-image=FILE
              use FILE as the boot image [default=boot.img]

       -c, --core-image=FILE
              use FILE as the core image [default=core.img]

       -d, --directory=DIR
              use GRUB files in the directory DIR [default=/boot/grub]

       -m, --device-map=FILE
              use FILE as the device map [default=/boot/grub/device.map]

       -r, --root-device=DEV
 Manual page grub-setup(8) line 5/47 63%


```

---

