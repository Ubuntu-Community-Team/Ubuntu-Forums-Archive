---
title: "USB mp3 player doesn't show up most of the time"
date: 2010-01-13
forum: Hardware
---

### Post by chojineke on 2010-01-13
After an upgrade from kubuntu 8.10 to 9.10 it won't show my mp3 player in the 'recently connected devices' applet anymore.. However once out of the x times I try connecting the device, it does show up and works perfectly.
A normal USB stick always shows up.

When the MP3 player is connected I can see with lsusb that it is found:
```
Bus 001 Device 010: ID 0471:2004 Philips
```in syslog I see this when connecting the device:
```
kernel: [ 2049.460051] usb 1-5: new high speed USB device using ehci_hcd and address 12
kernel: [ 2049.595235] usb 1-5: configuration #1 chosen from 1 choice
kernel: [ 2049.598307] scsi12 : SCSI emulation for USB Mass Storage devices
kernel: [ 2049.598517] usb-storage: device found at 12
kernel: [ 2049.598521] usb-storage: waiting for device to settle before scanning
```and nothing more...

When once out of x times it actually does see the mp3 player, this shows up:
```
kernel: [ 1695.624047] usb 1-5: new high speed USB device using ehci_hcd and address 9
kernel: [ 1695.759090] usb 1-5: configuration #1 chosen from 1 choice
kernel: [ 1695.764822] scsi9 : SCSI emulation for USB Mass Storage devices
kernel: [ 1695.765025] usb-storage: device found at 9
kernel: [ 1695.765029] usb-storage: waiting for device to settle before scanning
kernel: [ 1700.764243] usb-storage: device scan complete
kernel: [ 1700.766594] scsi 9:0:0:0: Direct-Access     Philips  SA33xx           0100 PQ: 0 ANSI: 4
kernel: [ 1700.767336] sd 9:0:0:0: Attached scsi generic sg4 type 0
kernel: [ 1700.807976] sd 9:0:0:0: [sdd] 945664 2048-byte logical blocks: (1.93 GB/1.80 GiB)
kernel: [ 1700.809252] sd 9:0:0:0: [sdd] Write Protect is off
kernel: [ 1700.809263] sd 9:0:0:0: [sdd] Mode Sense: 3e 00 00 00
kernel: [ 1700.809268] sd 9:0:0:0: [sdd] Assuming drive cache: write through
kernel: [ 1700.816159] sd 9:0:0:0: [sdd] 945664 2048-byte logical blocks: (1.93 GB/1.80 GiB)
kernel: [ 1700.819345] sd 9:0:0:0: [sdd] Assuming drive cache: write through
kernel: [ 1700.819358]  sdd: sdd1
kernel: [ 1700.841351] sd 9:0:0:0: [sdd] 945664 2048-byte logical blocks: (1.93 GB/1.80 GiB)
kernel: [ 1700.848638] sd 9:0:0:0: [sdd] Assuming drive cache: write through
kernel: [ 1700.848651] sd 9:0:0:0: [sdd] Attached SCSI removable disk
```It looks like if the device never becomes ready for the kernel to start scanning... However, when I connect the same device, using the same cable on my gentoo or debian machine, it is always found...As it was before in kubuntu 8.10... So I doubt that it is a hardware defect. There are also no actual errors in syslog, it just doesn't start scanning the device and assign a block device-file like /dev/sdd to it.

Does anybody else experience this kind of behaviour? Or does anybody know the cause of and maybe a solution to this?

---

### Post by rodisu on 2010-01-19
I have no idea what causes it, but I have the exact same problem with my sansa e260. I've always been able to connect to it with no problems in Ubuntu on my laptop, but when I try to connect to it in Kubuntu on my desktop it only works less than 10% of the time. I haven't even been able to figure out any kind of pattern for when it can connect and when it can't. It's been a problem for a few versions of Kubuntu now.

I'd also appreciate help on this, if anyone has any ideas.

---

### Post by jointstereotype on 2010-10-14
I've had a very similar issue with my Sansa e260 v2, under the Ubuntu 9.x and now 10.x series. (The player worked just fine with Ubuntu 8.10, oddly enough.) chojineke, my kernel log looks similar to yours when I try plugging my Sansa in.

On a whim, I tried switching to tty2, plugging my Sansa in, and then returning to GNOME with Alt+F7. There was a "not authorized" dialog, but the player was recognized in Nautilus. I tried cutting, copying, and deleting some files, and it seemed to work fine. So, the console trick seems to be a temporary workaround for now...

Any word on an official fix for this?

---

