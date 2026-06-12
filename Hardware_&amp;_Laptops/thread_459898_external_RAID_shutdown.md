---
title: "external RAID shutdown"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by lpaolini on 2007-05-31
Hi,

I'm running Feisty from an external Ultra320 SCSI RAID which is self powered.
When shutting down, the hard drives receive some kind of stand-by command (I hear them make a short sound in quick sequence) but they don't spin down.

I have tried the scsi-spin command from the scsitools (universe) package and it works perfectly, spinning down the drives as requested.

The problem is: if run the scsi-spin command from the /etc/init.d/halt script, just before the halt command, all the drives spin down correctly, but then after a few seconds they spin up again for loading /sbin/halt.

How could I solve that? Maybe chrooting to a ramdisk containing the necessary for completing the shutdown (mainly scsi-spin and halt)?

Thanks in advance for any help you could provide.

Luca

---

### Post by Tilo on 2007-05-31
ramdisk would be good, or use a Compact Flash card on an IDE-to-CompactFlash adapter.

I have my /boot partition on a CF card, and you could put some of your /sbin executables
on it as well... this would circumvent your problem..

---

