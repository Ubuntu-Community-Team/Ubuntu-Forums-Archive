---
title: "Xbox remote control?"
date: 2011-08-02
forum: Hardware
---

### Post by solouko on 2011-08-02
Okay, I'm having trouble installing my original Xbox remote controller on Ubuntu 10.4 64bit.  

I've installed LIRC according to [this guide]("http://www.mythtv.org/wiki/Ubuntu_lirc_install") but I need the custom conf files.

Following this [link and guide]("https://help.ubuntu.com/community/Xbox360Controller#Troubleshooting") I put into a terminal:

```
dmesg

```

And it returned this information on my IR devices.

```
[    6.388627] lirc_dev: IR Remote Control driver registered, major 61 
[    6.389683] 
[    6.389684] lirc_atiusb: USB remote driver for LIRC $Revision: 1.85 $
[    6.389685] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[    6.389708] lirc_dev: lirc_register_driver: sample_rate: 0
[    6.389748] lirc_atiusb[2]:  on usb4:2
[    6.389765] usbcore: registered new interface driver lirc_atiusb
[    6.405821] usbcore: registered new interface driver xpad
[    6.405823] xpad: X-Box pad driver
```

---

### Post by skatinjj on 2011-08-02
Here is a good site to start looking:

[forum.xbmc.org]("forum.xbmc.org")

---

### Post by solouko on 2011-08-02
Thanks, but I really wanted to avoid using a media centre application, I did find the configuration files on there though!

---

### Post by olabri on 2011-10-23
I think his point was that many xbmc users got the same problems, so it might be worth heading over there to see if someone has solved it.

---

