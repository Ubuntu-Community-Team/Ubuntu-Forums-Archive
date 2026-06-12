---
title: "Sony Vaio VPCP11S1E"
date: 2010-08-13
forum: Hardware
---

### Post by vivaeltopo on 2010-08-13
Hi there,
I just bought a "[Sony Vaio VPCP11S1E]("http://www.sonystyle.com/webapp/wcs/stores/servlet/CategoryDisplay?catalogId=10551&storeId=10151&langId=-1&categoryId=8198552921644608896&parentCategoryId=16154")" and installed Ubuntu on it.
Most things work out of the box but few things still need to be fixed:

Trackpoint - Touchpad:
At the moment both the Trackpoint and the Touchpad dont work.
xinput tells me:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Sony Vaio Keys                          	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sony Visual Communication Camer         	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```
"gpointing-device-settings" doesn't find any of them and the following two scripts didn't work either:
```
# /etc/X11/Xsession.d/99trackpoint

# Trackpoint Scrollfunktion für alle relevanten Eingabegeräte aktivieren
xinput list | \
        egrep 'Sony Vaio Jogdial|TPPS/2 IBM TrackPoint|DualPoint Stick|Synaptics Inc. Composite TouchPad / TrackPoint' | \
        sed 's/.*id=\([0-9]\{1,\}\).*/\1/' | \
        while read id ; do
                xinput set-prop $id "Evdev Wheel Emulation" 1
                xinput set-prop $id "Evdev Wheel Emulation Button" 2
                xinput set-prop $id "Evdev Wheel Emulation Timeout" 200
                xinput set-prop $id "Evdev Wheel Emulation Axes" 6 7 4 5 # horizontal und vertikal
                #xinput set-prop $id "Evdev Wheel Emulation Axes" 0 0 4 5 # nur vertikal
done

```
```
# xorg.conf.d script
Section "InputClass"
    Identifier      "Trackpoint"
    MatchProduct    "TPPS/2 IBM TrackPoint|DualPoint Stick|Synaptics Inc. Composite TouchPad / TrackPoint"
    MatchDevicePath "/dev/input/event*"
    Option          "EmulateWheel" "true"
    Option          "EmulateWheelButton" "2"
    Option          "EmulateWheelTimeout" "200" 
    Option          "YAxisMapping" "4 5"
    Option          "XAxisMapping" "6 7"
EndSection
```

Right now i am using an external mouse... any thoughts how to get this working?

The second but not that important thing is, the speakers wont work...
The sound card seems to be configured right, because if i plug in some headphones there is sound, volume is all right, no issues, but the build-in speaker doesnt do anything... i already checked the levels in "alsamixer".
Soundcard info:
```
10: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_811b
  Unique ID: u1Nb.RaFFXx_T1w8
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel System Controller Hub (SCH Poulsbo) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x811b "System Controller Hub (SCH Poulsbo) HD Audio Controller"
  SubVendor: pci 0x104d "Sony Corporation"
  SubDevice: pci 0x9073 
  Revision: 0x06
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0x942c0000-0x942c3fff (rw,non-prefetchable)
  IRQ: 19 (515 events)
  Module Alias: "pci:v00008086d0000811Bsv0000104Dsd00009073bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

Has anyone already found out how to get those things working on this notebook or could help me figure this out?

---

### Post by j3ffyang on 2010-09-08
I have the same issue here. Did you fix this issue? Thanks. J

---

### Post by j3ffyang on 2010-09-08
SOLVED by [http://vimalkumar.in/2010/08/16/ubuntu-10-04-on-the-sony-vaio-p/](http://vimalkumar.in/2010/08/16/ubuntu-10-04-on-the-sony-vaio-p/)

I verified in Lucid on my Vaio p115 laptop. Works perfect.

---

### Post by vivaeltopo on 2010-10-10
woohooo! thanks a lot ill try this tomorrow! :D

---

### Post by H8Ball on 2010-11-01
Is there a way to get the 3G-Modem running without running Windows again?
It was a lot of work to back-it-up and remove it.

Thanks for your Help

---

