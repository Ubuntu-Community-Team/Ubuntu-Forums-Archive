---
title: "when i plugin my ipod classic, nothing happens"
date: 2008-10-31
forum: Hardware
---

### Post by hachel on 2008-10-31
hi,
no sound, no popup, no icon on the desktop.
As seen in a couple of guides and howtos, here is the output of dmesg:
```
[ 9733.856205] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 9733.916555] sd 10:0:0:0: [sdc] Spinning up disk...<6>usb 1-2: USB disconnect, address 5
[ 9735.600024] .ready
[ 9735.600659] sd 10:0:0:0: [sdc] READ CAPACITY failed
[ 9735.600665] sd 10:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9735.600670] sd 10:0:0:0: [sdc] Sense not available.
[ 9735.604159] sd 10:0:0:0: [sdc] Write Protect is off
[ 9735.604166] sd 10:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 9735.604169] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[ 9735.611432] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[ 9735.612572] sd 10:0:0:0: Attached scsi generic sg3 type 0
[10353.808043] usb 1-2: new high speed USB device using ehci_hcd and address 6
[10353.962928] usb 1-2: configuration #1 chosen from 2 choices
[10353.986999] scsi11 : SCSI emulation for USB Mass Storage devices
[10353.994017] usb-storage: device found at 6
[10353.994025] usb-storage: waiting for device to settle before scanning
[10358.992236] usb-storage: device scan complete
[10359.000599] scsi 11:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[10359.066307] sd 11:0:0:0: [sdc] Spinning up disk......................................................................................................not responding...
```

blkid shows no ipod, mount shows no ipod, i installed the libgpod 3.x via synaptic (ubuntu 8.10).

any help?
thanks

hachel


EDIT: reinstalled ubuntu for various reasons and now it works
i think i installed and then removed some kde-package under gnome and with that it removed most of my media players, think it had something to do with that

PS: how do i set this topic to solved?

---

