---
title: "How to install ubuntu/kubuntu 9.04 from hard drive(iso image)"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by cool.aquarian on 2009-08-15
Hi..

I am planning to do fresh install of **kubuntu 9.04** on my old desktop.
I downloaded iso of the distribution, but do not want to burn it on a CD (already have **live cd of ubuntu 9.04**).
I tried creating live usb using unetbootin and booting from it, but it gives **boot error**. 
Maybe my desktop doesnt support booting from usb.

So is there a way to install kubuntu 9.04 using its iso image on my hard drive and live cd of ubuntu (9.04) ?

Please help.
Thank you.

---

### Post by presence1960 on 2009-08-15
The normal way is to install with all partitions unmounted. That's why you use a CD or usb drive. As someone else said on here before "you are trying to change your tires on your car while you are driving".

P.S. after creating bootable usb did you go into BIOS and set the boot order to boot from USB or as my BIOS does: my flash drive shows up in hard disk boot order. I move the flash drive to #1 position in the hard disk boot order. Then it boots.

---

### Post by cool.aquarian on 2009-08-15
> **presence1960 said:**
> The normal way is to install with all partitions unmounted. That's why you use a CD or usb drive. As someone else said on here before "you are trying to change your tires on your car while you are driving".

P.S. after creating bootable usb did you go into BIOS and set the boot order to boot from USB or as my BIOS does: my flash drive shows up in hard disk boot order. I move the flash drive to #1 position in the hard disk boot order. Then it boots.

Thanks for replying.
Yes, I did change USB to #1 priority, then the hard drive was below at #2.
When I do that, it shows failure message as **boot error**.
It means it is trying to boot from USB, but not able to do so.

So, apart from creating Live USB through Unetbootin in Windows,
[B]Do I need to change anything manually in isolinux.cfg/syslinux.cfg to get it to boot from USB(any settings specific to CDRom)?
Also I read somewhere that I also need to use syslinux to mark the USB Drive as active partition.

Could this be reason for this error?
[/B]

---

