---
title: "How to know which USB a device is using"
date: 2009-05-11
forum: Hardware
---

### Post by Tilex on 2009-05-11
Hi guys !

I've hooked up a receipt printer to a Jaunty PC (amd64) with a USB cable.

If I issue the command "lsusb", I get :
```
Bus 002 Device 005: ID 04b8:0202 Seiko Epson Corp. Receipt Printer M129C
```

So my computer recognizes it.  Now, in a certain configuration file, I must specify which "file" that printer is using to talk to my OS.

I guess it's one of the files in the "/dev/" folder that start with "tty" but I've got all of these:
```
tty    tty11  tty15  tty19  tty22  tty26  tty3   tty33  tty37  tty40  tty44  tty48  tty51  tty55  tty59  tty62  tty9   ttyS3
tty0   tty12  tty16  tty2   tty23  tty27  tty30  tty34  tty38  tty41  tty45  tty49  tty52  tty56  tty6   tty63  ttyS0
tty1   tty13  tty17  tty20  tty24  tty28  tty31  tty35  tty39  tty42  tty46  tty5   tty53  tty57  tty60  tty7   ttyS1
tty10  tty14  tty18  tty21  tty25  tty29  tty32  tty36  tty4   tty43  tty47  tty50  tty54  tty58  tty61  tty8   ttyS2

```

And also, I've got these files in /dev/ that start with "usb":
```
usb/            usbdev1.6_ep03  usbdev1.8_ep01  usbdev2.1_ep81  usbdev2.3_ep81  usbdev2.5_ep82  usbmon2
usbdev1.1_ep00  usbdev1.6_ep81  usbdev1.8_ep82  usbdev2.2_ep00  usbdev2.3_ep82  usblp0
usbdev1.1_ep81  usbdev1.6_ep82  usbdev1.8_ep83  usbdev2.2_ep81  usbdev2.5_ep00  usbmon0
usbdev1.6_ep00  usbdev1.8_ep00  usbdev2.1_ep00  usbdev2.3_ep00  usbdev2.5_ep01  usbmon1
```

Would someone happen to know which file is used for my EPSON printer ?  If I've got the bus address above, is that enough info to check which file controls it?

Thanks!

---

