---
title: "USB drives no longer being auto mounted"
date: 2012-01-20
forum: Hardware
---

### Post by ratcheer on 2012-01-20
I just noticed this problem a few minutes ago, but my guess is that it started with this morning's 3.0.0-15 kernel upgrade. Neither my external hard drive (Seagate 2 TB) nor removable "thumb drives" are being mounted, automatically. Both were working just fine until very recently.

I am able to manually mount the external hard drive, but I have never had to do this until now. And I am not sure how to manually mount a thumb drive. I have always been able to plug them in, they pop up in the Nautilus drive list, use them, safely remove them, plug another one in, etc, etc.

Is this a known bug with the new kernel? I would like to have my system act the way it did before. How can I fix it?

Tim

---

### Post by ratcheer on 2012-01-20
I found this article and tried to do as it instructs to automount USB drives. I installed gconf-editor and ran it, but when I navigated to /apps/nautilus/preferences, there is no entry named media_automount_open, nor anything similar to it.

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Tim

---

### Post by ratcheer on 2012-01-20
The system is detecting the thumb drive when it is inserted. It is just not mounting it like it is supposed to.

```
[ 1268.976526] usb 2-1.3: new high speed USB device number 5 using ehci_hcd
[ 1269.070468] scsi7 : usb-storage 2-1.3:1.0
[ 1270.069261] scsi 7:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[ 1270.069759] scsi 7:0:0:1: Direct-Access     SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[ 1270.268490] sd 7:0:0:0: Attached scsi generic sg7 type 0
[ 1270.268654] sd 7:0:0:1: Attached scsi generic sg8 type 0
[ 1270.269601] sd 7:0:0:0: [sdg] 3995648 512-byte logical blocks: (2.04 GB/1.90 GiB)
[ 1270.269990] sd 7:0:0:1: [sdh] 16384 512-byte logical blocks: (8.38 MB/8.00 MiB)
[ 1270.271097] sd 7:0:0:0: [sdg] Write Protect is off
[ 1270.271102] sd 7:0:0:0: [sdg] Mode Sense: 03 00 00 00
[ 1270.271673] sd 7:0:0:1: [sdh] Write Protect is on
[ 1270.271676] sd 7:0:0:1: [sdh] Mode Sense: 03 00 80 00
[ 1270.272167] sd 7:0:0:0: [sdg] No Caching mode page present
[ 1270.272171] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[ 1270.273012] sd 7:0:0:1: [sdh] No Caching mode page present
[ 1270.273017] sd 7:0:0:1: [sdh] Assuming drive cache: write through
[ 1270.277577] sd 7:0:0:0: [sdg] No Caching mode page present
[ 1270.277582] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[ 1270.278074] sd 7:0:0:1: [sdh] No Caching mode page present
[ 1270.278079] sd 7:0:0:1: [sdh] Assuming drive cache: write through
[ 1270.282106]  sdg: sdg1
[ 1270.283212]  sdh: sdh1
[ 1270.288055] sd 7:0:0:1: [sdh] No Caching mode page present
[ 1270.288060] sd 7:0:0:1: [sdh] Assuming drive cache: write through
[ 1270.288063] sd 7:0:0:1: [sdh] Attached SCSI removable disk
[ 1270.288591] sd 7:0:0:0: [sdg] No Caching mode page present
[ 1270.288596] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[ 1270.288600] sd 7:0:0:0: [sdg] Attached SCSI removable disk

```

From the above, I am pretty sure I can mount them as /dev/sdg1 and /dev/sdh1. But the point is, I shouldn't have to. Until today, this has always happened automatically.

Does anyone have any idea what is going on and/or how to fix it?

Thanks,
Tim

---

### Post by ratcheer on 2012-01-22
Bump.

Can't anyone help with this? How, in 11.10, am I supposed to configure the system to automount removable drives?

This worked until two days ago and just stopped.

Tim

---

### Post by madvinegar on 2012-01-23
Go to ```
etc/modules
```

and on top of the modules list add the line

```
usb_storage
```


It should look something like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

usb_storage
lp
lp
lp
lp
```


This is how I solved a similar problem.

Let me know what happened.

---

### Post by ratcheer on 2012-01-23
Thank you very much for your response, @madvinegar.

Several things:

First, that file has not been changed since 5-Aug-11, so I do not think it has anything to do with my problem over the past few days.

However, it does not have "usb_storage" in it, so I am adding it. I'll post back when I know what happens.

Finally, and mysteriously, my system started automounting the external drive again, this morning. I Have no idea what could have caused this, but it is good.

On the other hand, it still does not automount an inserted thumb drive. I will see if the change to /etc/modules helps that.

Thanks, again,
Tim

---

### Post by ratcheer on 2012-01-23
Ok, after adding usb_storage to /etc/modules and rebooting, both my external drive and my thumb drive are being automounted. So, problem solved.

However, why this happened is still a mystery. The modules file never had that in it before, and automount worked until a couple of days ago. Color me confused. :confused:

Thank you, @madvinegar.

Tim

---

### Post by madvinegar on 2012-01-23
The exact thing happened to me after a kernel update.
It did mount the devices only if they were plugged in before booting.
I was trying to find a solution for 3 days and I managed finally to get it done as I explained above.

Glad I could help my friend!

---

