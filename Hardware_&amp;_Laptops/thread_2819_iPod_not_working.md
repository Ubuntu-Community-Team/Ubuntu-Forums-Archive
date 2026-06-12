---
title: "iPod not working :|"
date: 2004-10-31
forum: Hardware &amp; Laptops
---

### Post by bitserf on 2004-10-31
hi,

i'm not too sure what the issue is here. my iPod used to work, and then, it just decided to stop working. i can't recall changing anything related to it, and i'm still running a stock kernel.

the symptoms: 

i plug in the ipod, and instead of seeing it pick it up as a SCSI disk, i see only this in dmesg:

ieee1394: Node added: ID:BUS[0-01:1023]  GUID[000a270002762d57]
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...

so it is seeing it, somewhat, but for some reason its not trickling through to the SCSI subsystem. i have all the scsi modules loaded (sd_mod, especially), as well as the sbp2 module. i took care to load them before plugging in the iPod.

i ran the "rescan-scsi-bus.sh" script that is floating around, to no avail.

Windows and FreeBSD can see and mount the iPod fine.

any ideas?

---

### Post by bitserf on 2004-10-31
I also reformatted and reloaded the firmware, thinking that may have been the problem. Still the same symptoms, so the problem must be the Ubuntu kernel.

---

### Post by bitserf on 2004-11-12
For anyone else who has this problem after me, the problem was with the Ubuntu kernel image I was using.

For some reason, the linux-image-2.6.8.1-2-686 kernel didn't support my Firewire properly, whereas the linux-image-2.6.8.1-2-386 kernel did.

Hope this helps.

---

