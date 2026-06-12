---
title: "gigaware webcam"
date: 2009-10-08
forum: Hardware
---

### Post by AvengingAngel718 on 2009-10-08
i got a cheap gigaware webcam from radioshack for 8 bucks, but it doesnt work in ubuntu. it is a model number 25-234. does anyone know how i might get it running, or could anyone suggest a cheap, reliable webcam that runs natively under linux?

---

### Post by nixscripter on 2009-10-11
Google can't find a driver, so one could start guessing.

Connect the camera, and run this command: ```
lsusb
``` You should see the device show up in the list (along with other USB devices you have plugged in), but it might not be clear as to what it is.

Look at the two groups of hex numbers seperated by a colon. Copy those, and then run this command to get more information:

```
lsusb -d **1234:ABCD**
```

with the numbers filled in. Post the results, which will be quite long, and that will help identify what it says it is. (Also, please put [code] forum tags around your output listing to keep it readable, as I have done for the commands above).

---

### Post by AvengingAngel718 on 2009-10-12
the only output i get from any of the usb devices listed when i run that is exactly what it says when i run lsusb, i.e. "Bus 002 Device 004: ID 06a3:8020 Saitek PLC" for my keyboard. I'm not sure my webcam is even listed because gigaware isn't the listed vendor name on any of my usb devices.

would there possibly be a driver wrapper that would let me just install the windows driver?

---

### Post by nixscripter on 2009-10-12
Unfortunately, no. The way device drivers are done on Windows is quite different from Linux. The only shot would be to ascertain that the device uses firmware loaded from userspace, in which case a Linux driver could load this firmware to the device fairy easily. However, that is still a job for the driver writer.

If you are having difficulty identifying the device, try this instead. Open a terminal, and run: ```
tail -0lf /var/log/messages
```

It may print system messages, or just hang. Plug the device in. You should see several messages from the usb driver, something like:

```
usb [COLOR="Red"]4-1[/COLOR]: new low speed USB device using uhci_hcd and address 2
```

The important thing is the first pair of numbers. This is the Bus and device number. In my case, it is bus 4. 

You can press Control-C to stop the log reading. Then, **lsusb** can take the bus number the device connected to:

```
lsusb -s [COLOR="Red"]4[/COLOR]
```

This output should be shorter. If you're still not sure, post the log messages which appeared.

---

