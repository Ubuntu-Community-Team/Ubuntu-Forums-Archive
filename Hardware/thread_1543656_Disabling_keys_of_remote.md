---
title: "Disabling keys of remote"
date: 2010-08-01
forum: Hardware
---

### Post by henriet on 2010-08-01
Hello,
I own this cheap remote ([link]("http://cgi.ebay.fr/USB-IR-media-fil-PC-Computer-Telecommande-393-/260565373201?cmd=ViewItem&pt=FR_JG_Informatique_Peripheriques_Claviers&hash=item3caae81111")), for which I made a driver for lirc.
The remote is partly recognized as a mouse and keyboard. I'd like xorg to ignore keys as they are already managed by lirc, but keep managing mouse moves. 
Is it possible to do so using udev or xorg.conf.d rules ?

Here is an extract from /var/log/Xorg.0.log :
```
[ 17827.773] (II) config/udev: Adding input device ATWF@83-W001 ESKY.CC USB_V3B (/dev/input/event3)
[ 17827.773] (**) ATWF@83-W001 ESKY.CC USB_V3B: Applying InputClass "evdev pointer catchall"
[ 17827.773] (**) ATWF@83-W001 ESKY.CC USB_V3B: Applying InputClass "evdev keyboard catchall"
[ 17827.773] (**) ATWF@83-W001 ESKY.CC USB_V3B: Applying InputClass "LocalKeyboard"
[ 17827.773] (**) ATWF@83-W001 ESKY.CC USB_V3B: always reports core events
[ 17827.773] (**) ATWF@83-W001 ESKY.CC USB_V3B: Device: "/dev/input/event3"
[ 17827.779] (II) ATWF@83-W001 ESKY.CC USB_V3B: Found 9 mouse buttons
[ 17827.779] (II) ATWF@83-W001 ESKY.CC USB_V3B: Found scroll wheel(s)
[ 17827.779] (II) ATWF@83-W001 ESKY.CC USB_V3B: Found relative axes
[ 17827.779] (II) ATWF@83-W001 ESKY.CC USB_V3B: Found x and y relative axes
[ 17827.779] (II) ATWF@83-W001 ESKY.CC USB_V3B: Found absolute axes
[ 17827.779] (II) ATWF@83-W001 ESKY.CC USB_V3B: Found keys
[ 17827.779] (II) ATWF@83-W001 ESKY.CC USB_V3B: Configuring as mouse
[ 17827.779] (II) ATWF@83-W001 ESKY.CC USB_V3B: Configuring as keyboard
[ 17827.779] (**) ATWF@83-W001 ESKY.CC USB_V3B: YAxisMapping: buttons 4 and 5
[ 17827.779] (**) ATWF@83-W001 ESKY.CC USB_V3B: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
```

Thanks.

---

