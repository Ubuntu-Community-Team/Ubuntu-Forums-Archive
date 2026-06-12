---
title: "Are Special Steps Needed After Replacing Motherboard?"
date: 2014-08-15
forum: Hardware
---

### Post by lambdafox on 2014-08-15
My motherboard got fried; so, I had to replace it.

I am a linux newbie, but have been using Windows XP for years.

In XP, when this happened, you needed to follow the following procedure before booting back in on your hard drive:

1. Boot into Safe Mode as administrator
2. Open Device Manager
3. Delete all devices
4. Reboot normally and allow windows to re-install all your hardware and drivers

Is there any similar procedure I need to follow before booting into Ubuntu GNOME 14.04 (amd64)?

Or special steps after boot I need to do?

Thank you!

---

### Post by Bucky Ball on 2014-08-15
No special steps required that spring to mind. Ubuntu should check the hardware on boot and utilise the appropriate drivers, if it has them.

You could, theoretically, take a functional Ubuntu drive from one machine and stick it in another and it should work just fine. At least that has been my experience. 

Good luck, and please report back. Curious to hear how it goes. ;)

---

### Post by TheFu on 2014-08-15
There is only 1 thing that likely needs correction after moving an install to different hardware - that is the udev rules for ethernet, since the onboard ethernet/wifi MAC addresses will change.  Everything else should work fine.

Just remove the eth* lines inside /etc/udev/rules.d/70-persistent-net.rules
The next reboot will add new versions back and all will be fine.

---

### Post by em3raldxiii on 2014-08-16
Depending on the age of the old motherboard versus the new one, you may have conflicting EFI boot rules, too.  If the machine fails to boot altogether, it might simply be a matter of disabling quick boot, Secure boot, and/or selecting Legacy boot in your BIOS.

---

### Post by TheFu on 2014-08-16
> **em3raldxiii said:**
> Depending on the age of the old motherboard versus the new one, you may have conflicting EFI boot rules, too.  If the machine fails to boot altogether, it might simply be a matter of disabling quick boot, Secure boot, and/or selecting Legacy boot in your BIOS.

Only 1 of my 7 systems uses EFI .... it is quite the hassle. Sorry didn't consider that. I'm worried about the day when I get to fight with that, though we have fought with it at installFests the last few years and will get to again in a few weeks (Sept InstallFest at ALE-NW).

---

### Post by em3raldxiii on 2014-08-16
Yeah, just last weekend I had a fight with a peculiar EFI arrangement for one of my co-workers.  It turns out I ended up having to copy the grub EFI boot config file to a fake Microsoft/Boot directory on the EFI partition, and the file had to be renamed to a Windows-centric name.  Apparently that particular HP computer will not boot from any other location than a /Microsoft/boot directory o.O

---

