---
title: "nokia pc suite alternative"
date: 2008-11-28
forum: General Help
---

### Post by justborn on 2008-11-28
i have a Nokia 3110 and i wanna use it to connect to the net.my service provider is Airtel(gprs),i am using ibex,can any one help me?

---

### Post by kecskemethy on 2008-11-28
fyi [http://tareqalam.wordpress.com/2008/07/11/connect-your-nokia-phone-with-linux-without-pc-suite/](http://tareqalam.wordpress.com/2008/07/11/connect-your-nokia-phone-with-linux-without-pc-suite/)

---

### Post by peakshysteria on 2008-11-28
```
lsusb
```gives me:
> Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 0421:045a Nokia Mobile Phones 6280 Phone Parent
Bus 001 Device 006: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 001 Device 005: ID 046d:c30e Logitech, Inc. UltraX Keys (X)
Bus 001 Device 004: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro
Bus 001 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 04cc:1521 Philips Semiconductors USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Which should give me:
```
sudo /sbin/modprobe usbserial vendor=0×421 product=0×45a
```
This returns:
```
FATAL: Error inserting usbserial (/lib/modules/2.6.27-9-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

```

How can I proceed from here on?

---

### Post by justborn on 2008-11-29
u see i just wanna to coonect to the net and not all the pc suite can do ,so cannot i jus use the _ibex_network manager>>select **mobile broadband**tab,and then add a connection as the connection wizard itself gives me the option of selecting my service provider.


the only doubt i have it this-"will it work?"

---

### Post by peakshysteria on 2008-11-29
justborn; give it a try. It should work fine without any problems (though I haven't tried this solution myself).

Myself, I would like to access everything on my phone. Right now it's urgent to get to my contact list so I can make a copy of it.

---

### Post by hariks0 on 2009-04-05
For connecting using Nokia Mobile, I just connect it with PC using the USB cable and the network manager automatically did the rest. Now I am posting this with my Nokia 6131 and Ubuntu 8.10.

What I would like to get is a Nokia PC Suite alternative with all function such as Data Sync, Bluetooth Connectivity, message and contacts manager etc.

---

