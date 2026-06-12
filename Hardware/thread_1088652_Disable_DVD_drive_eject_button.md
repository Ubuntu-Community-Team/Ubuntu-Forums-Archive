---
title: "Disable DVD drive eject button?"
date: 2009-03-06
forum: Hardware
---

### Post by kikazaru on 2009-03-06
I have a Lenovo T400, with a Matsushita Blu-Ray drive, and it happens rather frequently that when I stuff it into my rucksack the DVD drive button gets pressed and the tray pops out in a soon-to-be-snapped-off kind of way...

Surely one can prevent the button from being able to open the drive? I tried sysctl and set dev.cdrom.lock = 1 but this seems to have no effect. Likewise I tried a little C program which does an ioctl to set CDROM_LOCKDOOR, but this also doesn't seem to work.

I think there are three conditions that have some bearing: drive is empty, drive contains unmounted/blank disc, drive contains mounted disc.

Any ideas?


ps:

An incidental warning: the Matsushita drive has cr@ppy firmware level region coding enforcement, i.e., libdvdcss can't help you get round region coding because the drive itself won't even give you the encrypted data. Region coding is therefore insurmountable unless someone hacks the firmware. So I would advise:

Don't ever buy Matsushita/Panasonic optical drives if you can help it!

---

