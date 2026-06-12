---
title: "USB3 drive disconnecting"
date: 2013-11-08
forum: Hardware
---

### Post by Freek07 on 2013-11-08
This is driving me crazy. Brand new USB3 hard drive, I get this U1 and U2 errors after some time and the dirver then disconnects.
This is what happens (see attached log).
Is there anything I can do?

Nov  8 08:11:44 MayPad kernel: [44146.685588] usb 4-3: Disable of device-initiated U1 failed.
Nov  8 08:11:49 MayPad kernel: [44151.683110] usb 4-3: Disable of device-initiated U2 failed.
Nov  8 08:11:49 MayPad kernel: [44151.779055] sd 13:0:0:0: [sde] Unhandled error code
Nov  8 08:11:49 MayPad kernel: [44151.779063] sd 13:0:0:0: [sde]  
Nov  8 08:11:49 MayPad kernel: [44151.779066] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Nov  8 08:11:49 MayPad kernel: [44151.779069] sd 13:0:0:0: [sde] CDB: 
Nov  8 08:11:49 MayPad kernel: [44151.779071] Write(10): 2a 00 13 60 1b 20 00 00 1e 00
Nov  8 08:11:49 MayPad kernel: [44151.779084] end_request: I/O error, dev sde, sector 2600524032
Nov  8 08:11:49 MayPad kernel: [44151.795036] hub 3-0:1.0: unable to enumerate USB device on port 3
Nov  8 08:11:49 MayPad kernel: [44151.795064] usb 4-3: USB disconnect, device number 7
Nov  8 08:11:49 MayPad kernel: [44151.796766] sd 13:0:0:0: [sde] Unhandled error code
Nov  8 08:11:49 MayPad kernel: [44151.796774] sd 13:0:0:0: [sde]  
Nov  8 08:11:49 MayPad kernel: [44151.796777] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Nov  8 08:11:49 MayPad kernel: [44151.796780] sd 13:0:0:0: [sde] CDB: 
Nov  8 08:11:49 MayPad kernel: [44151.796783] Write(10): 2a 00 13 60 1b 3e 00 00 1e 00
Nov  8 08:11:49 MayPad kernel: [44151.796798] end_request: I/O error, dev sde, sector 2600524272
Nov  8 08:11:49 MayPad kernel: [44151.796839] Buffer I/O error on device sde1, logical block 85076764
Nov  8 08:11:49 MayPad kernel: [44151.796845] Buffer I/O error on device sde1, logical block 85076765
Nov  8 08:11:49 MayPad kernel: [44151.796849] Buffer I/O error on device sde1, logical block 85076766
Nov  8 08:11:49 MayPad kernel: [44151.796853] Buffer I/O error on device sde1, logical block 85076767
Nov  8 08:11:49 MayPad kernel: [44151.796856] Buffer I/O error on device sde1, logical block 85076768
Nov  8 08:11:49 MayPad kernel: [44151.796860] Buffer I/O error on device sde1, logical block 85076769
Nov  8 08:11:49 MayPad kernel: [44151.796864] Buffer I/O error on device sde1, logical block 85076770
Nov  8 08:11:49 MayPad kernel: [44151.796867] Buffer I/O error on device sde1, logical block 85076771
Nov  8 08:11:49 MayPad kernel: [44151.796871] Buffer I/O error on device sde1, logical block 85076772
Nov  8 08:11:49 MayPad kernel: [44151.796875] Buffer I/O error on device sde1, logical block 85076773
Nov  8 08:11:49 MayPad kernel: [44151.796878] Buffer I/O error on device sde1, logical block 85076774
Nov  8 08:11:49 MayPad kernel: [44151.796882] Buffer I/O error on device sde1, logical block 85076775

---

### Post by bazsound on 2013-11-08
I dont have a solution as i dont use USB 3 though my Ext HD is USB 3. If it supports USB2 try using USB 2 if it supports it. Not a fix but if it gets it working for now.

I dont like the look of those I/O errors on logical blocks which i usually see on faulty media like CD-roms and DVD's when it cant read the disk.. id confirm its working on another machine just to confirm the drive is OK.

---

### Post by Freek07 on 2013-11-08
Yeah, working on 2.0 would be a (slow) solution... and IO errors are because the drive disconnects and it doesn't exist anymore. Funny, it reconnects as new device (sdd -> sde -> sdf -> ....).
It happens when I copy a lot of data.

---

