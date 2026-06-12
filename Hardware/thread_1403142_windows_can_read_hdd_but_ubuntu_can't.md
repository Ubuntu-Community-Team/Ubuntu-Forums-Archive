---
title: "windows can read hdd but ubuntu can't"
date: 2010-02-09
forum: Hardware
---

### Post by yawnmoth on 2010-02-09
I have this drive that 2.5" SATA HDD that I can read just fine in Windows Vista but that I can't even see in GParted in Ubuntu 9.10.  Any ideas?  Here's what happens when I plug the drive in in Ubuntu:

```
[  683.808016] usb 1-6: new high speed USB device using ehci_hcd and address 8
[  683.864041] hub 1-0:1.0: unable to enumerate USB device on port 6
...
[  759.268020] usb 1-5: new high speed USB device using ehci_hcd and address 9
[  759.324059] hub 1-0:1.0: unable to enumerate USB device on port 5
```
Also, for the record, I don't care about the contents on the drive.  I just want to reformat it.  Sure, I can reformat it in Windows, but I don't believe I should have to.

Any ideas?

---

### Post by yawnmoth on 2010-02-12
*bump*

---

### Post by chewearn on 2010-02-12
does the SATA-to-USB comes with a external power source?  Perhaps the bus power is insufficient.

---

### Post by yawnmoth on 2010-02-15
> **chewearn said:**
> does the SATA-to-USB comes with a external power source?  Perhaps the bus power is insufficient.

It does.  Plus, it works in Windows - just not in Ubuntu.

Regardless, I borrowed another SATA-to-USB adapter from a friend and that one's working for me just fine, so even though my SATA-to-USB adapter works in Windows, maybe it just doesn't, any longer, work in Ubuntu?  I have no clue...

---

