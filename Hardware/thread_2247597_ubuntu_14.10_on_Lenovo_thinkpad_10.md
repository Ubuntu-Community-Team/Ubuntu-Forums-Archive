---
title: "ubuntu 14.10 on Lenovo thinkpad 10"
date: 2014-10-09
forum: Hardware
---

### Post by anurag-mehra1 on 2014-10-09
Installed ubuntu 14.10 on Lenovo Thinkpad 10.  Specs: Intel Atom Z3795 Processor, 4GB LPDDR3 Memory, 128GB eMMC Storage, 64bit OS. Touch screen, wifi do not work. If anyone has experimented with this tablet please respond. Thanks.

---

### Post by gordintoronto on 2014-10-09
What is the Wi-Fi adapter? On most laptops, the Wi-Fi adapter is actually connected as a USB device, and will appear when you run the command: lsusb.

I hope you also understand that Ubuntu 14.10 is still in testing, and has not been released.

---

### Post by Vladlenin5000 on 2014-10-09
> **gordintoronto said:**
> On most laptops, the Wi-Fi adapter is actually connected as a USB device, and will appear when you run the command: lsusb.

True... Until recently. Most Atom based tablets have it via SDIO.

---

### Post by anurag-mehra1 on 2014-10-12
Wifi adaptor is Broadcom BCM43241 2x2 a/b/g/n+BT, SDIO. I am aware that 14.10 is still in testing. Tried it to ensure that latest drivers were available. Have tried to check which chipset the touchscreen uses. Windows device manager does not give any useful information. Could not get any from a quick web search also. Ubuntu does not recognize the touch controller or the wifi chip. lsusb, lspci, lshw, dmidecode do not give any information on both devices. Thanks.

---

### Post by saou on 2014-10-31
Thanks for sharing your experience.  I am thinking of getting one of these primarily for writing; could you tell me how well the wacom digitizer works out of box?  How about screen rotation and (this is important) battery life?  Have you tried e.g. to use a usb-wifi dongle?  

THANKS!

---

### Post by anurag-mehra1 on 2014-10-31
In ubuntu, digitizer does not work neither does the touchscreen. Did not experiment with screen rotation but it remains stuck in landscape mode by default. Never ran it long enough in ubuntu to know of battery life (the battery applet did not work) but it seems to get hot pretty fast. In win8.1 everything works well: digitizer, rotation, good battery life. I did not try a wifi dongle on ubuntu bit I expect that any dongle that works with ubuntu should be fine.

---

### Post by saou on 2014-10-31
Thanks for your reply.  Regarding the machine getting hot pretty quickly:  Have you tried to install e.g. tlp?

[http://www.webupd8.org/2014/10/advanced-power-management-tool-tlp-06.html](http://www.webupd8.org/2014/10/advanced-power-management-tool-tlp-06.html)

It is like powertop, but better, and there are lenovo specific options that might help reduce power use.

Have you tried fedora?  It's more bleeding edge and might have drivers etc not yet incorporated into ubuntu (e.g. it supports plug-and-play displaylink devices almost 18 months earlier than ubuntu).  (edit: Looks like the beta for fedora 21 will come out Nov 4).

Please keep us informed of any progress/news!

---

### Post by anurag-mehra1 on 2014-11-01
Some luck! I finally tried the official release of 14.10 (my previous test was on a pre-release 14.10 in early october). Touchscreen works out of the box! Onboard works well. Wacom digitizer does not, wifi, bluetooth adpators not recognized, battery widget applet still red. Will work more and revert over the coming week. May try tlp and fedora at some point. Thanks for the pointers.

---

### Post by anurag-mehra1 on 2014-11-04
Fedora Live does not even boot. Also tried ubuntu 15.04 daily build. Same result. Touchscreen works, no digitizer, no wifi, bluetooth, battery applet. Not much luck solving the wifi or wacom problem yet.

---

### Post by saou on 2014-11-16
> **anurag-mehra1 said:**
> Fedora Live does not even boot. Also tried ubuntu 15.04 daily build. Same result. Touchscreen works, no digitizer, no wifi, bluetooth, battery applet. Not much luck solving the wifi or wacom problem yet.  Thanks for your update.  I just came across   [https://www.happyassassin.net/fedlet-a-fedora-remix-for-bay-trail-tablets/](https://www.happyassassin.net/fedlet-a-fedora-remix-for-bay-trail-tablets/) It seems to work (mostly) on various atom-based tablets, including dell venue pro 11 (atom), lenovo miix 2 and asus t100, but there is no mention of thinkpad 10.   Some people seem to have better luck with the early sept release than the latest one.

---

