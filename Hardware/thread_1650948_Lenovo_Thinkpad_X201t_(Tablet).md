---
title: "Lenovo Thinkpad X201t (Tablet)"
date: 2010-12-22
forum: Hardware
---

### Post by spamalam on 2010-12-22
Hey all, I want to permanently switch to kubuntu as my main operating system and intend to use the nasty microsoft apps I need to use in a VirtualBox VM.

However, I am having the following problems and am wondering if there is a step by step guide to solving:
[LIST]
[*]Web Cam not detected / working
[*]Thinkpad Touch Screen Monitor not detected
[*]Shutting lid locks instead of puts laptop to sleep
[/LIST]

**Web Cam not detected**
I don't seem to be able to use my webcam which is built into my laptop.  The following are the outputs from pci/usb device listings:
[jbriggs@jbriggs-x201 hotkey]$ lsusb
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 031: ID 17ef:4816 Lenovo 
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


[jbriggs@jbriggs-x201 hotkey]$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

However I see my camera under:
> 
[jbriggs@jbriggs-x201 hotkey]$ usb-devices 

...snip...

T:  Bus=01 Lev=02 Prnt=02 Port=05 Cnt=02 Dev#= 31 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=17ef ProdID=4816 Rev=23.45
S:  Manufacturer=Chicony Electronics Co., Ltd.
S:  Product=Integrated Camera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=200mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

...snip...


As you can see, it appears in usb-devices not lsusb.  I fired up chatroulette.com to troll but my camera is not listed.

**Thinkpad monitor not detected**

```

[jbriggs@jbriggs-x201 debian]$ xsetwacom list dev 
Serial Wacom Tablet eraser ERASER    
Serial Wacom Tablet stylus STYLUS

```

I'm pretty sure that should list my tft too?

**Shutting lid locks instead of puts laptop to sleep**

FN+F4 should suspend to ram, however it doesn't.  I bound this to sleep using KDE input manager, but when I close my laptop lid it locks rather than sleeps.

How can I change this?

---

### Post by Kirboosy on 2010-12-22
Hi! :)

For the webcam you should be able to open a Terminal/Konsole and type in **gstreamer-properties** . Since you can see the webcam as a USB device you should be able to set it as your default video capture....In theory at least ;)

It sounds like your locking instead of sleeping is a power setting. I'm not a big KDE user so I don't know how to navigate to your Power Management but there should be a setting in there that will fix it.

Any problems let me know.

---

### Post by spamalam on 2010-12-22
Ah!  Right about the power setting, under powermanagement it was set to lock.  Thank you.

No luck on the camera though.  Default is set to "test input", when I choose:
Video for Linux
Video for Linux 2
and hit test I get:
"Can not identify device /dev/video0"

---

### Post by Favux on 2010-12-22
Hi spamalam,

You should be able to get your touch working.  What release of Kubuntu are you using?  10.10, 10.04, or whatever?

Let's see if:
```
xinput --list
```
in a terminal shows touch in the output.  Post your output please.

---

### Post by spamalam on 2010-12-23
Apologies, I really should have posted the version I was on.  That was rather daft of me!

```

[jbriggs@jbriggs-x201 ~]$ uname -a
Linux jbriggs-x201 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
[jbriggs@jbriggs-x201 ~]$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```

```

[jbriggs@jbriggs-x201 ~]$ xinput --list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                     id=11   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                id=13   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                id=14   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera                         id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                    id=12   [slave  keyboard (3)]

```

---

### Post by Favux on 2010-12-23
Hi spamalam,

Sure enough no:
```
Serial Wacom Tablet touch
```
Does your X201t have single finger touch or multitouch (2FG; 2 finger)?  Does it work in Windows?  If multitouch do gestures work?

---

### Post by spamalam on 2010-12-23
> **Favux said:**
> Hi spamalam,

Sure enough no:
```
Serial Wacom Tablet touch
```
Does your X201t have single finger touch or multitouch (2FG; 2 finger)?  Does it work in Windows?  If multitouch do gestures work?

Its actually the direct sunlight with just pen.  The problem is pressure sensitivity with the pen, I downloaded several apps and none of them seems to work as I'd expect, and how it works in windows 7.  Windows 7 tablet is flawless.

Do you know an app that works:
* Detects Pen Sensitivity
* Detects which side of the pen is use (eraser or touch).

I figured this was a problem with the monitor detection as most guides show an extra device listed.

---

### Post by Favux on 2010-12-23
Hi spamalam,

If I understand you correctly you picked up a model without touch, correct?  So you just want your stylus working correctly, yes?

Let's start with Gimp.  Install it through Synaptic Package Manager since with Maverick it is no longer installed by default.  Then you need to configure your extended input devices.  See near the bottom of the Wacom wiki:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)  The other programs like Inkscape and Xournal will require something similar.  Then for the eraser point the eraser end to the little eraser icon and click on it so it is selected.  Then Save.  That will keep the assignment/selection of eraser for the eraser for then on.

You'll want to look at Xournal, CellWriter, EasyStroke, and MyPaint for your tablet.

Then to get finer control over your stylus and eraser you can use a xsetwacom script, .xsetwacom.sh.  I have a sample attached with the tablet pc package in post 2 at the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  If you don't have touch remove the touch sections and just leave the stylus and eraser sections.  See IV. in the HOW TO for installing it.

---

