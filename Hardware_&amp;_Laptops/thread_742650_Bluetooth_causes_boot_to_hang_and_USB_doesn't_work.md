---
title: "Bluetooth causes boot to hang and USB doesn't work"
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by cnirrad on 2008-04-01
I have a HP Pavilion dv6700 laptop. I have tried both Gutsy Gibbon and Hardy Heron (currently using Heron), and both versions will hang while booting on starting bluetooth. I have tried the kernel options "noapic irqpoll noirqdebug", but it still hangs. To get around this, I added "exit 0;" to the beginning of the bluetooth init script. This allows me to boot up fine, however when I plug in a USB iPod it doesn't mount. All I see in dmesg is:

```

[  128.833183] usb 7-2: new high speed USB device using ehci_hcd and address 5
[  128.845802] usb 7-2: configuration #1 chosen from 2 choices
```

It doesn't seem to be assigned to a device node such as /dev/sdb.

Also, if I do lsusb, the command just hangs.

Please help!

---

### Post by shuoink on 2008-04-01
I have a dv9700z with the same problem. I also added exit(0) to the bluetooth script so I could boot.

As far as the USB goes, I have found that it will work if the device is plugged in when my system is booting. If the device is not plugged in while booting, nothing will happen when you plug it in. Try that - I'd be interested to see if it works for you this way.

 I'm still searching for a solution to the usb problem and any help anyone can give would be much appreciated.

---

### Post by cnirrad on 2008-04-02
shuoink,

Thanks for the reply. I feel a little bit better knowing I'm not the only one :)

I found the following bit at [https://wiki.ubuntu.com/HP_dv6000_Series:](https://wiki.ubuntu.com/HP_dv6000_Series:)

> On the dv6510ef model, the uvcvideo driver completely breaks the Gutsy system (lsusb hangs, modprobe too, usb-storage doesn't work neither, so usb keys don't mount automatically...). For the moment, I just blacklisted the uvcvideo module and my system works like a charm.

I'm at work, so I won't be able to try this, or try booting with a USB device until later. If you get a chance, you might try blacklisting the uvcvideo to see if it fixes USB.

---

### Post by cnirrad on 2008-04-02
Good news!

Not only did booting with the USB device plugged in work, but blacklisting uvcvideo allows me to plug in a device that I didn't have in during booting.

---

