---
title: "Bluetooth Dongle not recognised"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by ashtond33 on 2008-01-18
Hey guys,
I have recently instailed Xubuntu on my OLPC XO laptop (forgive typing mistakes this thingi s tiny!). I plug in DBT-120 and lsusb does not show anything. I have installed the necessary packages, and this dongle does work with my other ubuntu machines. Thanks for the help!!

---

### Post by eggdeng on 2008-01-18
Run ```
dmesg | tail
``` just after you plug it in & post the output.

---

### Post by ashtond33 on 2008-01-18
[101564.021815] PM: Adding info for No Bus:usbdev2.11_ep00
[101564.021940] usb 2-3: configuration #1 chosen from 1 choice
[101564.024478] PM: Adding info for usb:2-3:1.0
[101564.024761] PM: Adding info for No Bus:usbdev2.11_ep81
[101564.024917] PM: Adding info for No Bus:usbdev2.11_ep02
[101564.025080] PM: Adding info for No Bus:usbdev2.11_ep82
[101564.025213] PM: Adding info for usb:2-3:1.1
[101564.025481] PM: Adding info for No Bus:usbdev2.11_ep03
[101564.025636] PM: Adding info for No Bus:usbdev2.11_ep83
[101564.025780] PM: Adding info for usb:2-3:1.2
olpc@OLPC:~$

---

### Post by eggdeng on 2008-01-19
Not much to go on there.:confused:

---

### Post by ashtond33 on 2008-01-19
My Ubuntu is running off a flash drive? Does that affect how it reads the other usb's

---

