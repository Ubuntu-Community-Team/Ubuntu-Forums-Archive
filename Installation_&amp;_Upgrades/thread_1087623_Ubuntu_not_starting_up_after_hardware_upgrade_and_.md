---
title: "Ubuntu not starting up after hardware upgrade and HDDs not seen by Live CD"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by badgerm on 2009-03-05
Hi guys,

This morning I upgraded my computer from an AMD 3200 to a C2D 3.16, necessitating a motherboard upgrade (though still an ASUS board). Whilst I just used the standard x86 version, I was expecting to have to reinstall Hardy, but I'm stuck between a rock and a hard place.

My mobo sees my three HDDs quite happily and after some playing around with the BIOS I was able to get GRUB up and start the boot process. This fails on the command

```
/build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-code.c: v2.6:USB HID core driver
```

or

```
sr 2:0:0:0: Attached SCSI generic sg0 type 5
```

depending on which kernel I use. Either way, the message is the same:

```
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT /dev/disk/by-uuid/fea3c8ff-8cad-4bf8-999b-20872b55598c does not exist. Dropping to a shell!
```

I'm then dropped out to ash. The path listed doesn't exist; the only thing in /dev/disk is `by-path'.

The most annoying part about all of this is that if I boot from the Live CD, none of my HDDs is detected. This is the case if I try to install from the CD too. There's no sda1, etc. in /dev and no drives are found when I try to install it as a result.

Any help would be much appreciated!

---

### Post by badgerm on 2009-03-05
Most depressingly of all, I've put in a Windows install disk and it's seeing all my drives just fine.

---

### Post by badgerm on 2009-03-05
Setting the SATA mode to AHCI in the BIOS sorted it out. Just need to reinstall now...

---

