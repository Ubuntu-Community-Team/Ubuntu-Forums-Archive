---
title: "HOWTO: Use Linksys WUSB54Gv2 in 10.04"
date: 2010-05-02
forum: Hardware
---

### Post by parm289 on 2010-05-02
I just wanted to document the process of installing/using the linksys usb wifi adapter WUSB54Gv2 here, so anyone out there with this adapter will have an easy time installing:

1. Download this firmware file for the p54usb driver: [http://daemonizer.de/prism54/prism54-fw/fw-usb/2.13.24.0.lm87.arm](http://daemonizer.de/prism54/prism54-fw/fw-usb/2.13.24.0.lm87.arm)

2. Rename the file to: ```
isl3887usb
```

3. Copy the isl3887usb file to /lib/firmware

4. Unplug/plug in the adapter and you should be able to successfully connect to the internet.

I have only tested this with unprotected networks - YMMV with WPA and WEP.

---

### Post by cor2y on 2010-05-18
Thank you for the tutorial i was going crazy trying to figure out why the network adapter refused to work in 10.04 while it worked fine in 9.10.

---

### Post by kmauser on 2010-06-12
Install linux-firmware-nonfree and it works:

sudo apt-get install linux-firmware-nonfree

The problem I'm having now is that the connection will disconnect frequently and then I have to reboot in order for it to work again.  This is with a WPA connection.

---

### Post by mfrazzz on 2011-12-23
Thanks parm289!  This worked perfectly and got me over a huge hurdle with little to no effort :)  I'm running Bodhi Linux (which is based on 10.04 LTS) on an old Dell PC and really didn't want to buy a new USB adapter.  This is connecting to a WPA2 Personal network so it works fine with protections.

---

