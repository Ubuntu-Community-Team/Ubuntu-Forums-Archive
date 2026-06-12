---
title: "Toggle power on/off for ultrabay harddrive"
date: 2011-09-14
forum: Hardware
---

### Post by kwan7zero on 2011-09-14
Hi everyone

I recently bought an ultrabay harddrive for my t410, but I was wondering, is it possible to somehow power on/off the harddrive, either with a script or a program? This is just so I can save some battery when the drive is unmounted and I'm unplugged.

Thanks!

- kenn

---

### Post by kwan7zero on 2011-09-16
bump?

Seriously, no one has ever given thought to this before? :(

---

### Post by bobstay on 2012-01-10
There is a script _[here]("http://www.thinkwiki.org/wiki/How_to_hotswap_Ultrabay_devices#Modern_systems_.28using_the_ahci_or_ata_piix_drivers.29")_ designed for ejecting the ultrabay device which you might be able to adapt. It would seem the sequence of events is:

[LIST]
[*]Unmount the drive
[*]hdparm -Y <device> to power it down
[*]Unregister the SCSI device with something akin to: "echo 1 > /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/delete" (may need changing for your system)
[*]echo 1 > $dock/undock (where $dock is somewhere in /sys/devices/platform)
[*]
[/LIST]

The first two might be enough for you, and the comments in the script suggest that if you only do the first two, the kernel should automatically issue the reset command to wake it up again when you next try to access it.

Of course I haven't actually *tried* any of this... I might do tonight!

---

