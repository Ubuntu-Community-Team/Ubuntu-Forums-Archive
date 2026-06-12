---
title: "Dell Latitude E6500 Bluetooth Module"
date: 2019-03-17
forum: Hardware
---

### Post by Redalien0304 on 2019-03-17
Looking install a Bluetooth Module for Dell Latitude E6500 that works with Ubuntu 18.04 Cinnamon DE.

---

### Post by Redalien0304 on 2019-03-19
Bump Anyone??

---

### Post by #&amp;thj^% on 2019-03-19
](*,) How about some more information, you will have to provide more than you have shown us thus far.
```
rfkill list
```

---

### Post by Redalien0304 on 2019-03-19
$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Laptop does not have a Bluetooth Module. Looking for Recommendations & how easy to Install One.

---

### Post by #&amp;thj^% on 2019-03-19
Most laptops come with built-in Bluetooth adapters, but even if yours doesn&#8217;t, external Bluetooth dongles are cheap and plentiful in supply. [https://www.thetechlounge.com/best-bluetooth-adapter/](https://www.thetechlounge.com/best-bluetooth-adapter/)

---

### Post by Redalien0304 on 2019-03-19
Not looking for Usb Type, would like the kind actually goes inside the laptop.

---

### Post by jeremy31 on 2019-03-19
If you want to use one of the Dell branded bluetooth modules, you might need to use usb-modeswitch to switch it from HID to HCI mode.  It has been a while since I have seen anyone ask about them

---

### Post by #&amp;thj^% on 2019-03-19
I don't know if you have slot for these but take a look: [https://www.parts-people.com/index.php?action=category&id=140&subid=232&refine=bluetooth](https://www.parts-people.com/index.php?action=category&id=140&subid=232&refine=bluetooth)

---

### Post by Redalien0304 on 2019-03-19
AS far know i do have "[COLOR=#000000]usb-modeswitch to switch it from HID to HCI mode" This laptop does not have any bluetooth card Installed.[/COLOR]

---

### Post by Redalien0304 on 2019-03-19
inxi -Fx Says i have Broadcom Limited BCM4312 802.11b/g LP-PHY

---

### Post by jeremy31 on 2019-03-19
I think most of the usb-modeswitch rules are in a compressed file in /usr/share/usb_modeswitch

---

### Post by yelvington on 2019-03-28
Modules are about five dollars on eBay. There is at least one YouTube video showing how to dismantle and replace or install the module. Once you watch it, you will conclude that the sane thing is to buy a USB dongle.

---

