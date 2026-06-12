---
title: "I need to switch off DMA for DVD in Hardy"
date: 2008-04-27
forum: Hardware
---

### Post by Zebidiah on 2008-04-27
Can anyone tell me how to switch of DMA in Hardy when I need to burn CD\DVDs (as it will cause the PC to hang otherwise.  This happens when using Knoppix and Windows as well unless DMA is turned off).
In Gutsy I used:
sudo hdparm -d0 /dev/hdb
with great success.

This no longer works.
I checked K3b and it says that the DVD burner is now /dev/scd0 which gives the following error:
sudo hdparm -d0 /dev/sdc
/dev/sdc: No such file or directory

and

sudo hdparm -d0 /dev/sdc0
/dev/sdc0: No such file or directory

Can anyone help?  Is there any further information that I can supply which may help?

---

### Post by shanek on 2008-04-27
You have:

sudo hdparm -d0 /dev/sdc0

when it should be:

sudo hdparm -d0 /dev/scd0

Unfortunately, it's a moot point. hdparm can't toggle DMA when IDE devices are used as scsi devices by the kernel.

---

