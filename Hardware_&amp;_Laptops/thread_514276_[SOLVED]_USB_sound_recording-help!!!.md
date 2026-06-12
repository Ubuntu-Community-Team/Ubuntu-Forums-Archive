---
title: "[SOLVED] USB sound recording-help!!!"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by NickArgyle on 2007-07-31
I just got my new Behringer UCA202 recording device today. On my laptop w/ feisty it shows up in the hardware manager when I plug it in, but it is not accessible in ALSA and does not show up in the output devices in audacity or JACK. I tried the device on my desktop pc, which has ubuntu studio, and, after installing a couple of packages through synaptic, it showed up in the I/O devices in audacity. I tried the same on my laptop and it made no difference. 

Any ideas on how to get it reecognized with ALSA or at least to show up in audacity or jack so I can record with it?

---

### Post by NickArgyle on 2007-07-31
bump

---

### Post by isaacj87 on 2007-07-31
Okay...you can try this suggestion:

Goto System>Preferences>Multimedia Systems Selector

in the "Default Input" section choose "USB Audio" from the drop-down menu.

If you can't see the Multimedia Systems Selector in Preferences you'll have to make it visible...

Press ALT+F2 and type alacarte...navigate on the left side to Preferences and on the right side select "Multimedia Systems Selector" to make it visible...

hope this helps.

---

### Post by NickArgyle on 2007-07-31
There is no usb option in that drop down box. Alsa must not be recognizing it. It is listed in my hardware manager as USB audio though.

---

### Post by NickArgyle on 2007-07-31
this is the info on it I get on it when I run hwinfo

```
66: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_8bb_2902_noserial_if0
  Unique ID: cLrx.SeUlILtBEE3
  Parent ID: k4bc.1nk5yKyqXL5
  SysFS ID: /devices/pci0000:00/0000:00:0b.0/usb1/1-2/1-2:1.0
  SysFS BusID: 1-2:1.0
  Hardware Class: unknown
  Model: "Burr-Brown USB Audio CODEC"
  Hotplug: USB
  Vendor: usb 0x08bb "Burr-Brown Japan, Ltd."
  Device: usb 0x2902 "USB Audio CODEC"
  Revision: "1.00"
  Speed: 12 Mbps
  Module Alias: "usb:v08BBp2902d0100dc00dsc00dp00ic01isc01ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #62 (Hub)

```

When I run asoundconf list there is only my nvidia card and my usb does not show. Is there a way to add the usb device (usb 0x2902?) to the alsa device list so I can connect it?

---

### Post by NickArgyle on 2007-07-31
????? anyone ???????

---

### Post by isaacj87 on 2007-07-31
when you see it in the Hardware Manager, does it appear as Raw USB device? or is it actually listed. It could eve say it's a USB Class-Compliant Audio Device or something.

---

### Post by NickArgyle on 2007-07-31
it says essential the same things as the above post. USB audio codec etc

---

### Post by isaacj87 on 2007-07-31
okay...And you sure that it doesn't show up in the setup portion of JACK control...

See the picture where I drew in red.

---

### Post by fredj on 2007-08-01
Stop jack. Open the alsa mixer and go to the File->Change Device menu. If it doesn't show up
there, its probably not a Ubuntu compliant USB sound device. Try searching for updated
firmware.

---

### Post by NickArgyle on 2007-08-01
Ok, figured it out. The usb modules were loading after the soundcard modules. I had to edit the modules so the USB stuff was first.
Thanks for the help.

---

