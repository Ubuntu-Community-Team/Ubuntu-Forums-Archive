---
title: "DVD and CD won't work"
date: 2010-05-18
forum: Hardware
---

### Post by j_arquimbau on 2010-05-18
Hello,

I've Ubuntu Lucid (64bits) installed in my computer. I cannot get DVDs nor CDs to be mounted. I have tried changing fstab file and adding piix module (don't know what is this last thing; I just saw it over there).

If I launch Brasero and I enter a virgin CD, it detects it as an empty CD but any record would fail.

dmesg:

[    0.815263] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T40N  JR03 PQ: 0 ANSI: 5
[    0.880032] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    1.039871] usb 1-5: configuration #1 chosen from 1 choice
[    1.145293] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.145298] Uniform CD-ROM driver Revision: 3.20
[    1.145419] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.145482] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.145602] ata2: port disabled. ignoring.

Does anybody know what all this is? Thank you!

---

