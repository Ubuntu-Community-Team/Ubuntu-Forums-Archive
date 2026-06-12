---
title: "Ubuntu installed on hd0,0 now trying to install Window Vista"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by mjma1977 on 2009-03-21
I formated my hard drive and split the drive into 2 partitions.  I installed Ubuntu 8.10 on hd0,0.  Now I am trying to install Windows Vista on hd0,1 but windows vista won't install because it can't write to the boot sector.  How can I get windows to install without formatting the hard drive and installing vista first?

---

### Post by mjma1977 on 2009-03-21
When you try to install Windows Vista, you may receive the following error message:
Windows is unable to find a system volume which meets its criteria for installation.
You experience this symptom if the following conditions are true:

    * In the BIOS, a universal serial bus (USB) removable device is set as the start device, or the USB removable device is set to a higher priority than the first hard disk drive in the start order.
    * You attach a non-bootable USB device to a USB port before you start the computer.
    * You try to install Windows Vista from DVD installation media. 

Back to the top
CAUSE
This issue occurs because the Windows Vista installation must be able to write t...
This issue occurs because the Windows Vista installation must be able to write to the boot volume of the computer, and the boot volume must be non-removable to prevent later removal of the boot device. If the boot device were removed, this would make it impossible for Windows Vista to start. A computer is restarted several times during installation. Because the BIOS reports the USB device as the boot device, and the USB device is removable, Windows Vista Installation cannot continue. This is by design.

---

### Post by mjma1977 on 2009-03-21
The above is why I can't install vista. Any suggestions other that starting over?

---

### Post by cholericfun on 2009-03-21
just a freak guess(letting the experts give a better go at it...)

the boot part is your forst patition.
thats where your boot files are send
siomehow it doesnt work with a ext3 cause win is blind to that.

so if you *can* try put ubuntu on the second partition and windows on the first and with ntfs or fat all should be well.

EDIT:
PS
you SHOULD install windows first cause it will wipe your boot sector clean off ubuntu,
with some work (check this forum) you'll be able to sort your boot manager to enable you to select either system but....
"work"

---

