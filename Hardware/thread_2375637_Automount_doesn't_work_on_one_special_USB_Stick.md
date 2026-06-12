---
title: "Automount doesn't work on one special USB Stick"
date: 2017-10-26
forum: Hardware
---

### Post by tobias-weinhold on 2017-10-26
Hello, 

i have one strange behaviour of detected. One of my USB-Sticks doesn't mount automatically. Ist's an U3 Stick. The strange thing is - if I go to console and open it there with fdisk or with gpartet, even if i don't change anything on the Stick he finds it and mounts it. It's not a big problem but an annoying one! ;) 

dmesg
```

[ 6162.059758] usb 3-3.4: new high-speed USB device number 7 using xhci_hcd
[ 6162.160417] usb 3-3.4: New USB device found, idVendor=0781, idProduct=5406
[ 6162.160421] usb 3-3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6162.160423] usb 3-3.4: Product: U3 Cruzer Micro
[ 6162.160425] usb 3-3.4: Manufacturer: SanDisk
[ 6162.160427] usb 3-3.4: SerialNumber: 087642053A11E413
[ 6162.160747] usb-storage 3-3.4:1.0: USB Mass Storage device detected
[ 6162.162173] scsi host6: usb-storage 3-3.4:1.0
[ 6163.168387] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer           8.02 PQ: 0 ANSI: 0 CCS
[ 6163.168802] sd 6:0:0:0: Attached scsi generic sg5 type 0
[ 6163.169466] sd 6:0:0:0: [sde] Attached SCSI removable disk
[ 6165.220842] sd 6:0:0:0: [sde] 31526911 512-byte logical blocks: (16.1 GB/15.0 GiB)
[ 6165.222865]  sde: sde1

```

lsusb
```

Bus 003 Device 007: ID 0781:5406 SanDisk Corp. Cruzer Micro U3

```

I already have changed the MBR; the Partition Format, the UUID.... nothing helped. I am nearly there to give it away. 

I startet many years ago with linux and know that automount is nothing with you really need - but nowadays i am used to it and don't wanne miss it! ;)

---

### Post by efflandt on 2017-10-26
It may have something to do with U3 which is a Windows executable for some sort of encryption on what appears to be a separate read-only CD/DVD like device which Linux would identify as an sr or sg device, along with whatever usb-storage partitions are on the memory stick. If you used U3 in Windows to encrypt the device, you would not be able to mount or read them in Linux. In your case dmesg does show sg5 (the read only partition) and sde with partition sde1, so not sure why those are not auto-mounted.

If you do not use the U3 encryption, you may want to look into possibly disabling that and see if it works any better: [https://askubuntu.com/questions/4653/how-do-i-get-rid-of-u3-system-on-my-usb-drive](https://askubuntu.com/questions/4653/how-do-i-get-rid-of-u3-system-on-my-usb-drive)

---

