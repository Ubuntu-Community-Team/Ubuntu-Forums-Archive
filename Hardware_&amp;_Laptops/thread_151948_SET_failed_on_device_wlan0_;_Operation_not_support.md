---
title: "SET failed on device wlan0 ; Operation not supported."
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by Emura on 2006-03-28
Hi all, this is the first time I've put in a real effort at attempting to run a Linux distro, and I've run into a problem. Ethernet settings are autodetected and work fine, but I'm having trouble with my wireless card.

Not knowing anything about this distro, I tried downloading, compiling, and installing the linux-wlan-ng drivers from the terminal to get my card to work. (Still don't know if that is my chipset, and didn't know about System > Administration > Networking). Going that method, I was able to activate the card with those drivers, but was never able to connect to my access point.

I came back sometime later and had forgotten completely how to reproduce what I had done before (loading the driver module) but discovered the Networking setup under System > Administration. I set all that up for my card (Ubuntu did identify that I had a wireless card attached), and found myself in the same situation as before. Card activated, but can't connect to access point. Tried deactivating WEP on the router, but no change.

The device is a USB wireless networking device and lsusb -v reports the idVendor as being "Acer (??)" and idProduct as "WarpLink 802.11b Adaptor."

The drivers loaded for the device are the prism2 drivers that I assume are included with the Ubuntu distro? Are they included with the distro might be a better question?

lshw shows the device, describing it as a "Wireless interface" with logical name "wlan0" capabilities "ethernet physical wireless" and configuration "broadcast=yes multicast=yes wireless=IEEE 802.11-DS"

I guess that's to be expected, since sudo iwlist wlan0 scan shows my accesspoint, but when I try to sudo iwconfig wlan0 essid HomeNet results in
```
Error for wireless request "Set ESSID" (8B1A) :
SET failed on device wlan0 ; Operation not supported.
```

sudo iwconfig wlan0 mode Managed results in the same thing. I'm guessing I don't have the proper driver for the card, and if that's the case, I don't know where to go from here.

Windows spoils me, I think. Thanks for any help!

---

### Post by Zeroedout on 2006-03-29
[quote=Emura]Hi all, this is the first time I've put in a real effort at attempting to run a Linux distro, and I've run into a problem. Ethernet settings are autodetected and work fine, but I'm having trouble with my wireless card.

Not knowing anything about this distro, I tried downloading, compiling, and installing the linux-wlan-ng drivers from the terminal to get my card to work. (Still don't know if that is my chipset, and didn't know about System > Administration > Networking). Going that method, I was able to activate the card with those drivers, but was never able to connect to my access point.

I came back sometime later and had forgotten completely how to reproduce what I had done before (loading the driver module) but discovered the Networking setup under System > Administration. I set all that up for my card (Ubuntu did identify that I had a wireless card attached), and found myself in the same situation as before. Card activated, but can't connect to access point. Tried deactivating WEP on the router, but no change.

The device is a USB wireless networking device and lsusb -v reports the idVendor as being "Acer (??)" and idProduct as "WarpLink 802.11b Adaptor."

The drivers loaded for the device are the prism2 drivers that I assume are included with the Ubuntu distro? Are they included with the distro might be a better question?

lshw shows the device, describing it as a "Wireless interface" with logical name "wlan0" capabilities "ethernet physical wireless" and configuration "broadcast=yes multicast=yes wireless=IEEE 802.11-DS"

I guess that's to be expected, since sudo iwlist wlan0 scan shows my accesspoint, but when I try to sudo iwconfig wlan0 essid HomeNet results in
```
Error for wireless request "Set ESSID" (8B1A) :
SET failed on device wlan0 ; Operation not supported.
``` 
sudo iwconfig wlan0 mode Managed results in the same thing. I'm guessing I don't have the proper driver for the card, and if that's the case, I don't know where to go from here.

Windows spoils me, I think. Thanks for any help![/quote]

You're on the right track, but the first thing you need to know is the chipset. So google the name and model of your card (or post here), and someone, somwhere will have posted what the chipset is. BTW, whenever you have a hardware problem, it's usually important to post the name and model of the hardware, makes things alot easier. If you did and i missed it, my apologies, my eyesight is shit and my attentionspan worse. Worse case sceneario, try the windows driver with ndiswrapper.

---

### Post by Emura on 2006-03-29
Oh jeeze, now I've gone and screwed things up. I downloaded the linux-wlan-ng package from the package manager (not sure if it had to be installed somehow or not) thinking that would be a better way to do things, since it worked with my nVidia 6600, but no. In lshw, the device still appears and is still tied to the prism2_usb driver, but it also says ```
*-network DISABLED
```

As you can expect, I can no longer scan, and my device does not appear in the GUI anymore.

The device is an "Inexq" model "UR012i" but shows up in Ubuntu as an "Acer (??) WarpLink 802.11b." I managed to get the case opened up and it looks like the chipset is made by ISL. The chip specifically says:
```
ISL
3871IK18
L0310KLWL
```
That's numerals 3871, letters IK, numerals 18, and letter L, numerals 0310, and letters KLWL. A google search revealed no useful information.

Edit: I'm dumb. I found a data sheet ([http://www.digchip.com/datasheets/parts/datasheet/235/ISL3871IK18.php](http://www.digchip.com/datasheets/parts/datasheet/235/ISL3871IK18.php)) that confirmed it will work with prism drivers. I'm just not sure where to go from here. My knowledge of Linux isn't high enough for most of the walkthroughs so I'm slowly working through O'Riely's "Running Linux" and reading Man pages, but I'd like to get this worked out so I can download packages I need to keep learning. ;)

---

### Post by Zeroedout on 2006-03-30
yes, your card does indeed work with the prism2 drivers. If you cannot get it working, I suggest you read the FAQ, [http://www.linux-wlan.com/linux-wlan/index.html#FAQ](http://www.linux-wlan.com/linux-wlan/index.html#FAQ) and i'm told this guide [http://www.fuw.edu.pl/~pliszka/hints/prism2.html](http://www.fuw.edu.pl/~pliszka/hints/prism2.html) can be helpfull. I'de go through things in more detail, but am currently under a tight schedual. If you do need to compile the latest drivers and can't seem to get it working, post back and i'll be happy to try and help out.

---

