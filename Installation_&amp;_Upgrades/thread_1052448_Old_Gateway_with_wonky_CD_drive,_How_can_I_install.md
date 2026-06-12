---
title: "Old Gateway with wonky CD drive, How can I install?"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by ThrobbingBrain66 on 2009-01-27
I aquired an old Gateway Solo 9300 laptop from a  friend of mine.  It had Windows 98 on it, but I'm trying to put linux on it.  Unfortunately I'm running in to one major problem: the CD drive is wonky.

It sounds odd, but I can only boot from the cd drive once or twice before it stops working.  After that, I have to leave the laptop alone for a while.  After I come back, it'll boot a few more times if I'm lucky.

The real problem happens when I actually do get a CD booted.  For some reason, after a seemingly random amount of time, the CD drive just drops the CD.  I get an error message about not being able to mount the CD drive and that the media may be missing.  After this happens, there's nothing I can do.

I've tried LiveCDs, alternate CDs, other distros, etc.  I've used md5sums to make sure my iso files and burns were good.

The one time I was able to fully boot a distro, I used Damn Small Linux.  I think I was only able to do this because I chose the option to load everything into RAM and run in from there.  Unfortunately, I couldn't get that to install (maybe something to do with the old kernel they use).

So, my question is, what else can I do to get Linux installed on this thing?

---

### Post by spcwingo on 2009-01-27
Does it support booting from USB?

---

### Post by boof1988 on 2009-01-27
Or... If the machine has a USB port but can't boot from it, maybe try the [USB Boot CD](http://www.pendrivelinux.com/category/usb-boot-cds/) at PenDriveLinux.  I haven't used one yet, but it looks like it might be able to help you since the CD drive is only used for boot-up.

---

### Post by r0g on 2009-01-28
Sounds like you could have more than one problem in play here. Have you given the HD a good formatting and sector check? Maybe it is just the CD though so best eliminate it anyway.

Simplest way is install UnetBootin and make a bootable USB key.

If it doesn't support USB boot but does have a NIC and PXE you can use this tutorial to boot the alternative CD over the LAN: [http://www.thehobbsfamily.net/how-tos/2008/07/28/setting-pxe-boot-server-under-ubuntu-hardy](http://www.thehobbsfamily.net/how-tos/2008/07/28/setting-pxe-boot-server-under-ubuntu-hardy)

These instructions are should be good for Intepid also, although Intrepid seems to have lost some support for older hardware so I'd recommend trying Hardy first.

---

### Post by ThrobbingBrain66 on 2009-01-28
> **boof1988 said:**
> Or... If the machine has a USB port but can't boot from it, maybe try the [USB Boot CD](http://www.pendrivelinux.com/category/usb-boot-cds/) at PenDriveLinux.  I haven't used one yet, but it looks like it might be able to help you since the CD drive is only used for boot-up.

This option is very promising but I keep getting dropped into BusyBox during boot.  I'll play around with this a bit more and let you know what I find.

Thanks!

---

### Post by Dark_AvengerX on 2009-11-06
> **ThrobbingBrain66 said:**
> This option is very promising but I keep getting dropped into BusyBox during boot.  I'll play around with this a bit more and let you know what I find.

Thanks!
I know whats up.

First your HDD may be failing.
Next is that the computer overheats.
Of course follow the help with the usb boot cd.

---

