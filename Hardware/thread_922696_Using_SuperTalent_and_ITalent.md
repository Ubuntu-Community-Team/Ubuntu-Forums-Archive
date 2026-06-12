---
title: "Using Super*Talent and I*Talent"
date: 2008-09-17
forum: Hardware
---

### Post by MaindotC on 2008-09-17
I just got the [Super*Talent]("http://www.supertalent.com/products/mp3_detail.php?type=VIDEGO28 MP4") and [I*Talent](http://www.ewiz.com/detail.php?name=MP4_l21BU) from ewiz.com.  The iTalent mounts as a USB drive which is fine, and I can send/receive files just fine.  The Super Talent doesn't mount, though.  Here're my logs:

syslog
```

Sep 17 15:43:27 z9432cjkl234a-desktop kernel: [33132.155853] usb 3-2: new full speed USB device using uhci_hcd and address 3
Sep 17 15:43:32 z9432cjkl234a-desktop kernel: [33137.314847] usb 3-2: config 1 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 0, changing to 6
Sep 17 15:43:32 z9432cjkl234a-desktop kernel: [33137.314859] usb 3-2: config 1 interface 0 altsetting 1 endpoint 0x81 has an invalid bInterval 0, changing to 6
Sep 17 15:43:32 z9432cjkl234a-desktop kernel: [33137.314866] usb 3-2: config 1 interface 0 altsetting 2 endpoint 0x81 has an invalid bInterval 0, changing to 6
Sep 17 15:43:32 z9432cjkl234a-desktop kernel: [33137.314872] usb 3-2: config 1 interface 0 altsetting 3 endpoint 0x81 has an invalid bInterval 0, changing to 6
Sep 17 15:43:32 z9432cjkl234a-desktop kernel: [33137.314879] usb 3-2: config 1 interface 0 altsetting 4 endpoint 0x81 has an invalid bInterval 0, changing to 6
Sep 17 15:43:32 z9432cjkl234a-desktop kernel: [33137.314885] usb 3-2: config 1 interface 0 altsetting 5 endpoint 0x81 has an invalid bInterval 0, changing to 6
Sep 17 15:43:32 z9432cjkl234a-desktop kernel: [33137.314892] usb 3-2: config 1 interface 0 altsetting 6 endpoint 0x81 has an invalid bInterval 0, changing to 6
Sep 17 15:43:32 z9432cjkl234a-desktop kernel: [33137.314898] usb 3-2: config 1 interface 0 altsetting 7 endpoint 0x81 has an invalid bInterval 0, changing to 6
Sep 17 15:43:32 z9432cjkl234a-desktop kernel: [33137.333972] usb 3-2: configuration #1 chosen from 1 choice
Sep 17 15:43:32 z9432cjkl234a-desktop NetworkManager: <debug> [1221680612.796686] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4d6_65e_noserial'). 
Sep 17 15:43:32 z9432cjkl234a-desktop NetworkManager: <debug> [1221680612.956351] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4d6_65e_noserial_if0'). 

```

lsusb
```

Bus 003 Device 003: ID 04d6:065e Mentor Graphics

```

I haven't tried installing the driver with ndiswrapper yet.  Can anyone suggest a way to get this working?  Thanks!

---

### Post by MaindotC on 2008-09-23
*bump*

---

### Post by MaindotC on 2008-11-19
I got this figured out.  I mount it using msdos filesystem and I can read/write to it.  The latest software runs and works perfectly in wine, but the video clips are shortened to 15 seconds :(  Anyone wanna give this a try I suggest it - neat little device and great price.

---

