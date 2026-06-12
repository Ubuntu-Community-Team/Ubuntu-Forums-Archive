---
title: "USB Flash Drive - Data Recovery - Drive Won't Mount?"
date: 2012-05-13
forum: Hardware
---

### Post by Sardien on 2012-05-13
Hi all,

I've got a friend's flash drive that appears to be dead but I'm trying to recover data off it for them.

When I plug it in I get the following from dmesg:

> [15919.096021] usb 1-5: new high speed USB device using ehci_hcd and address 7
[15919.229535] usb 1-5: configuration #1 chosen from 1 choice
[15919.229846] scsi5 : SCSI emulation for USB Mass Storage devices
[15919.230095] usb-storage: device found at 7
[15919.230098] usb-storage: waiting for device to settle before scanning
[15924.228197] usb-storage: device scan complete
[15924.228774] scsi 5:0:0:0: Direct-Access     GENERIC  USB Mass Storage 1.00 PQ: 0 ANSI: 2
[15924.229593] sd 5:0:0:0: Attached scsi generic sg3 type 0
[15924.235283] sd 5:0:0:0: [sdc] Attached SCSI removable disk


And that's all. 

I tried to mount it manually without luck:

> 
user@PC:mkdir /mount/flashdrive
user@PC:/mnt$ sudo mount /dev/sdc /mount/flashdrive
mount: /dev/sdc: unknown device


In Disk Utility it detects it as "GENERIC USB Mass Storage Device" but under "Volume information" all it says is "No Media Detected".

I've also tried plugging it into a Windows machine - the drive recognises a USB device but doesn't mount it.


Any way to recover the data please?

Thank you :)

---

### Post by fjgaude on 2012-05-13
The only thing that comes to mind is that the HHD is truly dead. The USB interface is alive and that's it.

If you could open the box up you might find that the connections are lose. Try re-connecting the SATA interface connections, two of them, one power, the other data.

---

### Post by Sardien on 2012-05-13
> **fjgaude said:**
> The only thing that comes to mind is that the HHD is truly dead. The USB interface is alive and that's it.

If you could open the box up you might find that the connections are lose. Try re-connecting the SATA interface connections, two of them, one power, the other data.

Hi fjguage,

Thanks for the reply.

Unfortunately it is a USB Flash drive (thumb/pen drive) and not an external USB HDD, no there are no SATA connections to try :(

---

### Post by fjgaude on 2012-05-13
Gosh, from all you have stated it sounds like a bad flash drive, period.

Try;

```
sudo mount -a
```

and if that doesn't do it, you are toast.

---

