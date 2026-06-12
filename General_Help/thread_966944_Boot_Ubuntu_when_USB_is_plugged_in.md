---
title: "Boot Ubuntu when USB is plugged in?"
date: 2008-11-01
forum: General Help
---

### Post by DaFunks on 2008-11-01
I would like to have Ubuntu and Windows on my laptop. The issue i have is that I use TrueCrypt and it would be a BIG pain to set it up with both as Grub causes issues when using a dual boot.

As my family normally use Windows I would need it to be #1 as the booting OS... So an idea that prang to me was that I could have Grub or whatever is best on my USB. I set USB Booting as #1 in the BIOS and then when I put my USB stick in it would boot Ubuntu which his on my hard drive (Not usb stick)

Could this be done? if so how would I go about doing it?

Just so I am clear.

a. Ubuntu and Windows would be on the same hard drive.
b. Grub (Or whatever booting system I use) would be on the USB stick.
c. When booting without the GRUB USB Stick in it would boot to Windows.
d. When USB stick is placed in, it would boot to Ubuntu

Any tips, help would be great

---

### Post by DaFunks on 2008-11-01
No help? Please?

---

### Post by rbmorse on 2008-11-01
Is possible.  You have to make sure your BIOS allows booting from a USB device and that you can set the boot device priority order so the machine tries to boot from the USB device before the internal hard drive. 

Install Windows first, make sure the machine boots normally into whatever flavor of winders is installed. 

When you install Ubuntu make sure the USB device is connected. When the installer gets to the partitioning routine select manual partitioning.  Enter the appropriate location options, then click on the "advanced" button on the partitioner page and tell it to install GRUB on the USB drive.  Complete the installation normally. 

When the installer reboots the machine enter BIOS setup and set the boot options to permit booting from a USB device and the boot device priority to try to boot from the USB before the internal hard drive.  

Make sure the USB device is inserted, then save the BIOS changes, which will reboot the machine.

---

### Post by rbmorse on 2008-11-01
I think a better alternative would be to install GRUB to the MBR of the hard drive and just set it to default to windows, and set the delay to a very short interval -- say 3 or 5 seconds.  That way, when the machine is turned on it will go to windows by itself unless you intervene as soon as the GRUB menu appears.

---

### Post by caljohnsmith on 2008-11-02
> **DaFunks said:**
> 
a. Ubuntu and Windows would be on the same hard drive.
b. Grub (Or whatever booting system I use) would be on the USB stick.
c. When booting without the GRUB USB Stick in it would boot to Windows.
d. When USB stick is placed in, it would boot to Ubuntu

It is possible to do exactly what you want to do; I've had the opportunity to help a few other people do it, so I know it can work. From a terminal (applications > accessories > terminal), first start with:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition on your internal sda drive as (hd0,X), where X is the partition number minus one, e.g. sda3 = (hd0,2). Now assuming your USB stick is drive sdb, then you would do:
```
grub> device (hd0) /dev/sdb
grub> device (hd1) /dev/sda
grub> root (hd1,X)
grub> setup (hd0)
grub> quit
```
Next reboot, make sure you BIOS is set to boot the sdb USB drive, and you should get the Grub menu; selecting any of the OSes though in the Grub menu should result in a Grub error like error 17. That will be easy to correct, but see if you can get this far first, and we can work from here. Otherwise let me know if you run into problems. :)

---

