---
title: "How I got my 6950 card (partially) working, should work for all 69XX 68XX cards"
date: 2011-01-24
forum: Hardware
---

### Post by logophobia on 2011-01-24
This is a small guide as to how I enabled the fglrx drivers for my 6950 card on ubuntu 10.10 with the newest (at this moment) 12.10 drivers.

* Add the following PPA to your sources list: ppa:ubuntu-x-swat/x-updates
* Install the drivers: sudo apt-get install fglrx
* Create the file /etc/X11/xorg.conf . Put the following minimal configuration there to force the driver:

```
Section "Device"
 Identifier "Card0"
 Driver "fglrx"
EndSection
```

* Reboot

X should now start with the new driver. You can use the catalyst control center to configure your desktop/card.

It will still show a "AMD Unsupported hardware" logo. There are a couple of hacks to get rid of this: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Unsupported_Hardware_Watermark](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Unsupported_Hardware_Watermark) . I haven't tried them myself.

More info on the drivers at this wiki: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

Important: A new revision of the drivers should be coming out soon which should support the new cards. This info may be out of date when you read it. Also, follow this guide at your own risk.

What doesn't work:
* Suspend
* Some glitching when in compiz

---

