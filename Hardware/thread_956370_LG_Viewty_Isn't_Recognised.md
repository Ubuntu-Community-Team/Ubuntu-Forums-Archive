---
title: "LG Viewty Isn't Recognised"
date: 2008-10-23
forum: Hardware
---

### Post by Devineman on 2008-10-23
When I plug in my LG Viewty phone (in 'Mass Storage' mode) in to the USB port, the Viewty claims it is connected, but Ubuntu doesn't find it.

I know I will have to manually mount it (like I did with a OneTouch), but Ubuntu isn't storing the drive anywhere that I can find. Can anybody help me please?

---

### Post by doktormiod on 2008-12-11
I got the same problem and haven't found solution yet :/

---

### Post by cariboo on 2008-12-11
Run dmesg in a terminal after you have plugged your device in and see if Ubuntu assigns it a device label. If it is assigning a device label you should see something like this:

```
[ 9646.670187] sd 6:0:0:0: [sdc] Write Protect is off
[ 9646.670189] sd 6:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 9646.670192] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 9646.670198]  sdc: sdc1
[ 9646.779347] sd 6:0:0:0: [sdc] Attached SCSI removable disk
```

As you can see my usb device is assigned /dev/sdc1

Jim

---

### Post by nbound on 2009-04-26
mine is recognised with the old 256MB card i got with my old nokia, but the new 2GB card i got is not recognised by ubuntu?

---

### Post by Pinecone_ on 2009-05-25
I also have this problem. looking in the output of dmesg i saw this (although i dont know if this has any relevance to the problem... could someone tell me how i can check somehow?)

[13322.976017] usb 3-2: new full speed USB device using uhci_hcd and address 14
[13323.096014] usb 3-2: device descriptor read/64, error -71
[13323.320026] usb 3-2: device descriptor read/64, error -71
[13323.536015] usb 3-2: new full speed USB device using uhci_hcd and address 15
[13323.656018] usb 3-2: device descriptor read/64, error -71
[13323.880017] usb 3-2: device descriptor read/64, error -71
[13324.096032] usb 3-2: new full speed USB device using uhci_hcd and address 16
[13324.508026] usb 3-2: device not accepting address 16, error -71
[13324.620031] usb 3-2: new full speed USB device using uhci_hcd and address 17
[13325.036027] usb 3-2: device not accepting address 17, error -71
[13325.036047] hub 3-0:1.0: unable to enumerate USB device on port 2

edit: plugging the viewty into a different usb port on my computer worked. Other things (flash drives, usb mice, etc) still work in the port that the viewty does not.

---

