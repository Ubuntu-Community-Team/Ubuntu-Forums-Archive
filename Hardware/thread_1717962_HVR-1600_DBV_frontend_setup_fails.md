---
title: "HVR-1600 DBV frontend setup fails"
date: 2011-03-30
forum: Hardware
---

### Post by emunson on 2011-03-30
I just got a new HVR-1600 and I can't seem to get it working, after boot I do not see any /dev/videoX entries.  This is what (I think) is relevant out of dmesg:
```
[    2.825396] cx18:  Start initialization, version 1.4.0
[    2.825440] cx18-0: Initializing card 0
[    2.825442] cx18-0: Autodetected Hauppauge card
[    2.856121] cx18 0000:04:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.862499] cx18-0: cx23418 revision 01010000 (B)
[    3.090905] cx18-0: Autodetected Hauppauge HVR-1600
[    3.090907] cx18-0: Simultaneous Digital and Analog TV capture supported
[    3.281658] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[    3.285741] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[    3.285745] DVB: registering new adapter (cx18)
[    3.366598] cx18-0: frontend initialization failed
[    3.366802] cx18-0: DVB failed to register
[    3.366885] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[    3.366915] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[    3.366949] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[    3.367418] cx18-0: Error -1 registering devices
[    3.371137] cx18-0: Error -1 on initialization
[    3.371183] cx18: probe of 0000:04:01.0 failed with error -1
[    3.371301] cx18:  End initialization

```

I have an nvidia graphics card and found the vmalloc idea but that has not helped (my kernel command line has vmalloc=256M)

Any ideas?

---

### Post by emunson on 2011-03-31
Bueller?

---

### Post by emunson on 2011-04-01
This message was caused by Hauppage changing the DVB frontend on the newer cards.  Support for the newer cards was added in commit: e3bfeabbf5ba5da7f6cc5d53a83cb7765220c619

Follow these instructions to build the latest drivers and it should work:
[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

---

