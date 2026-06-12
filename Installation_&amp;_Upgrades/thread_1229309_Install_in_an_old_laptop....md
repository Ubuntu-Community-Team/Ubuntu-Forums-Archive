---
title: "Install in an old laptop..."
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2009-08-01
My mate has an old Fujitsu e series laptop (circa 2002)
It has no CD-Rom and will not boot via USB

So the 2 main way's of installing Linux are ruled out!

Any Ideas on how to install a modern Linux on to a Laptop with only a floppy drive??

Is there still floppy installers around that will boot and allow an install via USB?

Or 

How to dd and ISO image of an installer disk onto a partition of the drive so it boots the installer and can install it to the rest of the drive?

all suggestions welcomed... ^_^

---

### Post by GolemdX on 2009-08-01
Hmm. When you say USB you mean USB CD/DVD-ROM drive?

I had this problem, but the CD drive on my laptop started working again.

But, this website looks promising: [http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)

I think it's too boot from linux installed on a flash drive, but you can probably boot from the flash drive to install. It seems to work with Mac OS X...

---

### Post by tgalati4 on 2009-08-01
Purchase a notebook drive to IDE adapter then plug it into the ribbon cable of a desktop machine.  Install from the desktop to the notebook drive.  Put drive back into the labtop and boot.  You may have to edit /boot/grub/menu.lst to get the proper root disk drive (most likely /dev/sda1).

I did this once on a seriously old hp omnibook.

---

### Post by solitaire on 2009-08-02
> **GolemdX said:**
> Hmm. When you say USB you mean USB CD/DVD-ROM drive?

I had this problem, but the CD drive on my laptop started working again.

But, this website looks promising: [http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)

I think it's too boot from linux installed on a flash drive, but you can probably boot from the flash drive to install. It seems to work with Mac OS X...

It will not boot from USB (not an option in the BIOS) so booting from Flash or USB CD-Rom will not work..

---

### Post by Sef on 2009-08-02
You could install via [networking]("https://help.ubuntu.com/community/Installation").

---

### Post by lindsay7 on 2009-08-02
> **tgalati4 said:**
> Purchase a notebook drive to IDE adapter then plug it into the ribbon cable of a desktop machine.  Install from the desktop to the notebook drive.  Put drive back into the labtop and boot.  You may have to edit /boot/grub/menu.lst to get the proper root disk drive (most likely /dev/sda1).

I did this once on a seriously old hp omnibook.


This is what you would use.

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2329300&Sku=M501-1220](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2329300&Sku=M501-1220)

You can also find them on Ebay for about $10.


If you unplug the drive on the computer that you are going to use to make the installation on the laptop drive, it will be set up as the hd(0,0) drive and partition. So when you put it back into the laptop, it should be good to go, if the laptop video and sound card are compatable with Ubuntu.

---

