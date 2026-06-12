---
title: "computer exiting X to login screen"
date: 2006-07-22
forum: Hardware &amp; Laptops
---

### Post by strattonbrazil on 2006-07-22
While my computer is running normally, after several minutes (I watched a whole DVD fine once), it will go black with a little white cursor like it's processing, then I'll see the nVidia logo and then I'll be shot to the login screen.  

I found an error in the last part of the X log.  Maybe someone could interpret it for me:

(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found
ProcXCloseDevice to close or not ?
SetGrabKeysState - disabled

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4a86]
1: [0xffffe420]
2: /usr/lib/xorg/modules/extensions/libglx.so [0xb7c60eee]
3: /usr/bin/X(FreeClientResources+0xa1) [0x806fde5]
4: /usr/bin/X(CloseDownClient+0x1bd) [0x80851ab]
5: /usr/bin/X(Dispatch+0x2ab) [0x8085e33]
6: /usr/bin/X(main+0x47c) [0x806e0a8]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d6fea2]
8: /usr/bin/X(FontFileCompleteXLFD+0x81) [0x806d611]

Fatal server error:
Caught signal 11.  Server aborting

---

