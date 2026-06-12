---
title: "Use USB-bluetooth-adapter instead of the on-board-bluetooth-adapter"
date: 2015-09-26
forum: Hardware
---

### Post by cookie-crisp on 2015-09-26
Hi there,
in the past I had troubles connecting a bluetooth-device while using wifi.
I figured out that using bluetooth and wifi at the same time lowers the wifi-speed.
So I ordered a bluetooth-usb-adapter and my plan was to disable the bluetooth-device in Ubuntu and then plug in the new usb-adapter and use this to connect my bluetooth-devices to.
This worked fine on Windows but on Ubuntu I had problems finding the device name to disable.
I use wifi and bluetooth through a mini-pcie card (Intel AC 7260, my mainboard is a Gigabyte H97N-WIFI.
The usb-adapter is a no-name-device from the internet.

I hope someone know how to figure this out.

Kind regards,
Phil. ;)

---

### Post by jeremy31 on 2015-09-26
Post the result of ```
lsusb
``` in terminal

---

### Post by cookie-crisp on 2015-09-26
Should be some on the Intel devices but I didn't found something the last time.

> Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 1038:1364 Ideazon, Inc. 
Bus 003 Device 004: ID 8087:07dc Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



---

### Post by jeremy31 on 2015-09-26
This worked for me when I tested ```
gksu gedit /etc/udev/rules.d/81-bluetooth-disable.conf
```

Then copy this and paste it into the file, this needs to be 1 line
```
[COLOR=#3F3F3F][FONT=Courier 10 Pitch]SUBSYSTEM=="usb", ATTRS{idVendor}=="8087", ATTRS{idProduct}=="07dc", ATTR{authorized}="0"[/FONT][/COLOR]
```[COLOR=#3F3F3F][FONT=Courier 10 Pitch]

Save, exit gedit and reboot

The 07dc is the bluetooth part of the 7260 wifi[/FONT][/COLOR]

---

### Post by cookie-crisp on 2015-09-26
Thank you very much.
But it doesn't work. I plugged out the dongle while listening to music and it kept playing music. Ergo it seems that it's still using the 'onBoard'-dongle.
How can I validate that the usb-bluetooth-dongle is in use?
And you did you figured out that 07dc is the bluetooth part of the 7260 wifi? Is there a terminal command?

[FONT=arial]This seemed to really solve the problem: > sudo gedit /etc/udev/rules.d/81-bluetooth-hci.rules and pasting this [/FONT]> [COLOR=#3F3F3F][FONT=Courier 10 Pitch]SUBSYSTEM=="usb", ATTRS{idVendor}=="8087", ATTRS{idProduct}=="07dc", ATTR{authorized}="0"[/FONT][/COLOR][FONT=arial]

in.
After I restarted my computer I had to set up my bluetooth device again.
[/FONT]

---

### Post by jeremy31 on 2015-09-26
> **behm-phil said:**
> Thank you very much.
But it doesn't work. I plugged out the dongle while listening to music and it kept playing music. Ergo it seems that it's still using the 'onBoard'-dongle.
How can I validate that the usb-bluetooth-dongle is in use?
And you did you figured out that 07dc is the bluetooth part of the 7260 wifi? Is there a terminal command?

It was a while back that I searched for that info on my 7260 wifi, it may have been using ```
usb-devices
``` and then looking through the results for bluetooth or btusb, the bluetooth module and finding the vendor/product id in the results

If it works, use the thread tools menu at the top of the page to 'mark as solved'

Thanks

---

