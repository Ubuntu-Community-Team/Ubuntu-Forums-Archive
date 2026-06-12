---
title: "spdif output with advanced mini dock from lenovo t400"
date: 2009-09-18
forum: Hardware
---

### Post by deadball on 2009-09-18
Hey guys.

Long i've been waited, but now it's on my desk; lenovo t400 with advanced mini dock. The notebook shall substitute my desktop PC completely except for gaming.

So i need the SPDIF cinch output for my receiver to watch dvd, tv and hear good music. Unfortunately there is no sound coming out of the boxes :'(

There are no checkboxes to activate the spdif via Ubuntu 9.04.

Some Specs:
```

jan@t400:~$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: CONEXANT Analog [CONEXANT Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: Conexant Digital [Conexant Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
jan@t400:~$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, Conexant Digital
    IEC958 (S/PDIF) Digital Audio Output

```  
```

jan@t400:~$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc020000 irq 17

```
```

jan@t400:~$ sudo hwinfo --sound
27: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_293e
  Unique ID: u1Nb.kXwNWe4doZB
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801I (ICH9 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293e "82801I (ICH9 Family) HD Audio Controller"
  SubVendor: pci 0x17aa "Lenovo"
  SubDevice: pci 0x20f2 
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfc020000-0xfc023fff (rw,non-prefetchable)
  IRQ: 17 (8389 events)
  Module Alias: "pci:v00008086d0000293Esv000017AAsd000020F2bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

[[IMG]http://img441.imageshack.us/img441/9364/screenshotubuntuubuntu.th.png[/IMG]](http://img441.imageshack.us/i/screenshotubuntuubuntu.png/)

In a german forum someone said something about OSSv4, could that be a solution?

Does anyone have an idea? This digital sound output is essential, otherwise i will bring the hardware back to my reseller :(

Thanks for all answers!

---

### Post by deadball on 2009-09-19
No ideas ? :)

---

### Post by deadball on 2009-09-21
In gentoo there shall be a way, at least with t61:confused: 

any other ideas?

---

