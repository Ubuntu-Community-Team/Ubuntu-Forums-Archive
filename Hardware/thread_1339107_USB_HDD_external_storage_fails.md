---
title: "USB HDD external storage fails"
date: 2009-11-27
forum: Hardware
---

### Post by igurug on 2009-11-27
I have a problem with my external USB HDD storage. Once it is connected to the USB, it is detected by the system and is mounted. However, after about 10 seconds of copying it fails, apears to be ummounted and the USB-cable is needed to be reconnected for further work.

The syslog at crash is following:
```

Nov 27 11:37:06 kimpa kernel: [  269.304063] usb 1-3: reset high speed USB device using ehci_hcd and address 2
Nov 27 11:37:11 kimpa kernel: [  274.436187] usb 1-3: failed to restore interface 0 altsetting 0 (error=-110)
Nov 27 11:37:11 kimpa kernel: [  274.437091] usb 1-3: USB disconnect, address 2
Nov 27 11:37:11 kimpa kernel: [  274.441169] sd 4:0:0:0: Device offlined - not ready after error recovery
Nov 27 11:37:11 kimpa kernel: [  274.441193] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 27 11:37:11 kimpa kernel: [  274.441199] end_request: I/O error, dev sdb, sector 16215331
Nov 27 11:37:11 kimpa kernel: [  274.441218] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 27 11:37:11 kimpa kernel: [  274.441223] end_request: I/O error, dev sdb, sector 16215347
Nov 27 11:37:11 kimpa kernel: [  274.441242] Buffer I/O error on device sdb1, logical block 15174708
Nov 27 11:37:11 kimpa kernel: [  274.441246] lost page write due to I/O error on sdb1
Nov 27 11:37:11 kimpa hald[5620]: forcibly attempting to lazy unmount /dev/sdb1 as enclosing drive was disconnected
Nov 27 11:37:11 kimpa kernel: [  274.524488] hub 1-0:1.0: unable to enumerate USB device on port 3
Nov 27 11:37:11 kimpa kernel: [  274.531623] FAT: unable to read inode block for updating (i_pos 242795335)
Nov 27 11:37:11 kimpa hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 0

```I've tried it under Windows and it works well. Then I surfed the interned for solution and found the proposition to disable the module "ehci_hcd". After this the fails were gone but the USB was working as USB 1.1 and the speed was too slow.

Does somebody know the way of tuning the ehci_hcd to solve the problem?

---

