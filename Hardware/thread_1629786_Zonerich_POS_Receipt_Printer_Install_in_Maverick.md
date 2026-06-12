---
title: "Zonerich POS Receipt Printer Install in Maverick"
date: 2010-11-24
forum: Hardware
---

### Post by nicknefarious on 2010-11-24
One and all,

I have just bought a Zonerich (Chinese Brand) POS Receipt Printer Model No. AB-T88 (USB).

I have connected it to an XP Virtual Machine (Maverick 64-bit host laptop, XP 32-bit Guest) and been able to install it easily and successfully printed a test message from here. 

I have been unable to install it however in Ubuntu Maverick as I am unsure of the process to follow. I have tried in CUPS and it doesn't seem to be recognised.

As well as installing it in Maverick I want to make use of it through FloreantPOS (An open source POS system). I didn't actually try to print a receipt from the printer with Floreant installed in the XP VM yet.

I have Floreant installed and working in Ubuntu Maverick 32-bit Desktop but without the printer it's virtually useless.

Can anyone direct me as to how I can install this printer. Do I need drivers? I have some drivers provided by the manufacturer though I didn't need them when installing in XP. It was instantly recognised.

I also noticed in the Virtualbox USB connections that the printer was being recognised as Zonerich Printer - so some connection was being made there... but how do I get from that to adding it as a printer and being able to print from it using Floreant in Maverick? At the moment I can't see or select the printer to configure it in Floreant. Floreant is java-based.

Any help or direction is much appreciated.

Cheers,

Nick

---

### Post by nicknefarious on 2010-11-25
Please... anyone???

I have five driver files for the printer. Three .dll files - ZT80_V5R127_UI.dll, ZT80_V5R127_UNI.dll and ZT80_V5R127.dll, a .ini file - ZT80_V5R127.ini and a .gpd file - ZT80_V5R127.gpd.

Thanks,

Nick

---

### Post by nicknefarious on 2010-12-01
Really... so there is not one Ubuntu soul out there willing and able to help here? That's pretty sad....

---

### Post by nicknefarious on 2010-12-07
F Bump

---

### Post by nicknefarious on 2010-12-11
FUbuntu Bump

---

### Post by nicknefarious on 2010-12-13
Below is the syslog output when I connect the USB printer. PLease can someone take a look at this and tell me what the problem is... I can almost see it myself. How do I fix it?

> Dec 13 17:30:12 mavericks-main udev-configure-printer: remove /devices/pci0000:00/0000:00:12.1/usb4/4-1
Dec 13 17:30:12 mavericks-main kernel: [19977.800744] usb 4-1: USB disconnect, address 4
Dec 13 17:30:15 mavericks-main kernel: [19980.900525] usb 4-1: new full speed USB device using ohci_hcd and address 5
Dec 13 17:30:15 mavericks-main kernel: [19981.067140] usb 4-1: config 1 has an invalid interface number: 1 but max is 0
Dec 13 17:30:15 mavericks-main kernel: [19981.067144] usb 4-1: config 1 has 2 interfaces, different from the descriptor's value: 1
Dec 13 17:30:15 mavericks-main kernel: [19981.067149] usb 4-1: config 1 interface 0 altsetting 0 has 1 endpoint descriptor, different from the interface descriptor's value: 2
Dec 13 17:30:15 mavericks-main udev-configure-printer: add /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0
Dec 13 17:30:15 mavericks-main udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:12.1/usb4/4-1
Dec 13 17:30:15 mavericks-main udev-configure-printer: Device vendor/product is 0483:5740
Dec 13 17:30:16 mavericks-main udev-configure-printer: Failed to fetch Device ID
Dec 13 17:30:16 mavericks-main udev-configure-printer: invalid or missing IEEE 1284 Device ID 

Thanks,

NN

---

### Post by nicknefarious on 2010-12-20
MMmmm ... Ubuntu - Strong, vibrant, resourceful community...

Over 360 views and not one reply or comment.

Thanks...

---

### Post by spam12345 on 2012-04-08
Sorry for digging up an old thread, but I'm planning to buy a cheap Chinese POS printer and may be about to have the problem.

I wonder if the problem is solved?

---

### Post by omarabbas on 2012-06-10
Hello

i have been struggeling with this same problem for over a week now. i wanted to use Lemon pos in my store, it being a wonderful pos software. but my reciept printer is also zonerich. and let me tell you, there is absolutely no way you can run it on anything other than windows. 
so i hesitated about getting another brand, but after a little research i fear that there is almost no thermal reciept printer supported by cups.
so my last resort was buying windows and also buying a new pos software not half as useful or pretty as Lemon.

one happy day, windows will die and it's remaining users will be the ones struggeling with hardware drivers. but untill that day, i guess it's windows in my store.

---

