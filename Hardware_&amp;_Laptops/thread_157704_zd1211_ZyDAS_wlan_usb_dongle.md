---
title: "zd1211 ZyDAS wlan usb dongle"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by cusco on 2006-04-09
TRYING TO MAKE A WLAN USB STICK WORK ZyDAS 1211 chipset

hi.. I have this usb stick.. I don't know its brand.. it looks like the cheapest generic thingie.. its transparent plastic and insite on the top of the chip I can read:

ZyDAS

ZD1211B-QF
d213k. 1
0540

and it looks just likein this pic: [http://www.zydas.com.tw/product/image/appzd1211-3.jpg](http://www.zydas.com.tw/product/image/appzd1211-3.jpg) (the lower green one)

I also have a cd with a driver utilitty for windows.. but it has no brand what so ever (like asus, trust, any of that) 
and its usbid is: 0ace:1215 ZyDAS
which is not on the supported hardware on [http://www.ubuntuforums.org/newthread.php?do=newthread&f=98](http://www.ubuntuforums.org/newthread.php?do=newthread&f=98)

I have downloaded the driver, compiled and installed with no problems. lsmod shows me the module is loaded but wlan0 cannot be found... :(

also dmesg shows:

[4295020.167000] ZD1211 802.11b/g USB WLAN driver v20050315 loaded
[4295020.167000] (c) Willig, Yang, Zviskov et al.
[4295020.167000] [http://zd1211.sourceforge.net/](http://zd1211.sourceforge.net/)
[4295020.168000] usbcore: registered new driver zd1211
[4295037.484000] usb 3-3: USB disconnect, address 3
[4295040.690000] usb 3-3: new high speed USB device using ehci_hcd and address 4

and lsmod shows:

root@Portatil:/home/cusco/Desktop/zd1211-driver-r71# lsmod |grep zd
zd1211                206624  0
usbcore               129668  5 zd1211,usbhid,ehci_hcd,uhci_hcd


I don't know what to do.. can I get some help? thanks

---

