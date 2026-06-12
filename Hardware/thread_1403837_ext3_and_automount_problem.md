---
title: "ext3 and automount problem"
date: 2010-02-10
forum: Hardware
---

### Post by WDYSUN on 2010-02-10
Dear Friends

I just formatted an external Western Digital hard drive of 1TB. First of all I find strange that GParted reports that the brand new formatted disk  has 14.81GB of used space,  is that possible that the only ext3 partition information take almost 15GB of space? I might be wrong but sounds stange to me. 

Than I have another question. I put a label, "wdisk", to my new hard drive. Now when I plugin the usb ubuntu recognizes the disk and it puts a link on the desktop named with the disk name, ie wdisk... but the disk is mounted in /media/usb0 and this directory is owned by root. There is any way to force Ubuntu to automount the disk in /media/wdisk where the latter directory has user privileges?

I would appreciate any help. Thanks in advance
Pierre

---

### Post by RedSingularity on 2010-02-10
Right click the drive when its on your desktop and select preferences.  Then go to the Drive tab and rename it there.  It will say something like /media/_______<Put name here]

---

### Post by WDYSUN on 2010-02-11
thanks a lot!
Pierre

---

### Post by SecretCode on 2010-02-11
> **WDYSUN said:**
> I just formatted an external Western Digital hard drive of 1TB. First of all I find strange that GParted reports that the brand new formatted disk  has 14.81GB of used space,  is that possible that the only ext3 partition information take almost 15GB of space? I might be wrong but sounds stange to me. 

Yes, that happens - this is either the "journal" or the "root reserved" space.

---

