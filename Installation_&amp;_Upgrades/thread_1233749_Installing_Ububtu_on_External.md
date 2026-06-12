---
title: "Installing Ububtu on External"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by AmerNewbieInDE on 2009-08-07
Is it possible to install Ubuntu 9.04 on an external USB SATA Hard Drive, not as live, but so it does nothing to my windows disk?

---

### Post by Herman on 2009-08-07
Yes, it is possible.
I don't really recommend it, but it's possible. 
If you want a portable Ubuntu installation, a USB flash memory stick is much better than a USB hard disk drive.

There are a few reasons in favour of keeping hard disk drives in computer cases.
Hard disk drives have a motor and bearings which generate heat. Normally, that heat is given off by conduction and radiation. This heat is absorbed by the air around the hard disk and normally is blown away by the computer's case fans. Most USB external hard drive caddies I have seen don't have any fans, so I don't know how they keep the hard disk drive inside cool when it's working hard. Probably they're only designed for file storage, and not for sustained use such as when we have an operating system running in them. It might depend on the ambient temperatures in your computer room or office though. Where I live it can get quite hot sometimes and even computer case temps need watching.
The maximum speed for the USB2 interface is only about 60 MBps, compared with 150 MBps you'd get if you removed your SATA hard drive from it's external case and secure the same drive in a hard drive bay inside your PC and plug it in directly via a SATA cable.
Also, hard disc drives are fragile, especially while the disc is spinning. It's unlikely you'll be picking up your desktops case or even your laptop while the computer is running, but it's easy to forget the USB external disc is still spinning when you're looking for that lost paperwork you need urgently somewhere in that pile on your desk.

With a flash memory stick you wouldn't have any of those problems.

However, I do own USB external hard drives myself with Ubuntu installed in them, so if you still want to do it now that you're aware of the arguments against doing so, just install Ubuntu in the normal way, except when you get to step 7 of 7 during the installation, click 'advanced' and choose to install the boot loader to the MBR of your USB drive, not to the first hard disk's MBR.

When you reboot, you'll need to use either your BIOS boot menu, or a boot loader/manager on a CD or floppy disk to get your USB to boot.

There are some illustrated step-by-step examples of how to install Ubuntu in my sig link, and they all show how to control where you install the boot loader.

Regards, Herman :D

---

### Post by phr33k-dc on 2009-08-07
i am running ubuntu 9.04 and i click on the usb startup disk creater. it wont let see the .iso image or my usb key??? is their any other way?

---

### Post by Herman on 2009-08-07
The good thing about the kind of Ubuntu you get when you use 'USB Startup Disc Creator' or 'LveCD' type of USB installs is that they have an 'Install icon', and you can use them to install Ubuntu in computers that don't have a CD/DVD drive.
If you do it that way, you won't need to worry about flash memory wear at all if you installed Ubuntu in flash memory. Your flash memory stick will last forever, (in theory).

If you just install Ubuntu in your USB flash memory stick or external hard drive in the same way as if tyou were installing to a normal hard disk, you'll have a normal installation. I don't beleive flash memory wear as anywhere near as big an issue as some people like to pretend. It probably will wear our someday, but that depends on what you use it for and how many hours per week. None of mine have worn out yet so I don't know.
I think it's best to just install Ubuntu.

---

### Post by AmerNewbieInDE on 2009-08-07
herman.. thanks for the reply and thanks for the warning, but i knew about the possible problems with the external drive. I will try it though.

---

