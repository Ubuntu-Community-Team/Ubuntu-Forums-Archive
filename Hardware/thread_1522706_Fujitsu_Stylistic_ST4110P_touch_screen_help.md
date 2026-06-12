---
title: "Fujitsu Stylistic ST4110P touch screen help?"
date: 2010-07-02
forum: Hardware
---

### Post by calraith on 2010-07-02
As the title indicates, I have a Fujitsu Stylistic ST4110P and can't get the touch screen to work.  It's possible that the touch device is simply dead in the hardware, though.  Can I get some help confirming or rejecting that hypothesis?  (I picked the computer up at a yard sale with no battery, RAM or hard drive for $40, so I haven't actually ever seen the touch screen work in Windows or otherwise.)  There's nothing relevant disabled in the BIOS as far as I can tell.

Anyway, I've been all over a dozen tutorials, and this is what I've done so far.  I have a fresh install of Lucid (the Netbook edition, which is absolutely brilliant) with all updates including kernel 2.6.32-23-generic installed.  The output of
```
sudo dmesg | grep ttyS
```is blank -- there is no output.  (grepping tty without the S in /var/log/messages only shows me lines regarding the tty0 console.)

I added the [Ubuntu-x-swat PPA]("http://www.ubuntuupdates.org/ppas/27") so I could install xserver-xorg-input-fpit.  I've seen references to a [patch for the fpit driver]("https://help.ubuntu.com/community/FujitsuStylisticST4000") but that patch seems to be for version 1.1 of the driver; whereas current is 1.3.   The 1.3 source will not compile with that patch, so I'm trusting that whatever fix the patch contained has since been incorporated.  I installed setserial as well.

Contents of /etc/serial.conf:
```
/dev/ttyS0 uart 16550A port 0x0220 irq 4 low_latency baud_base 115200 spd_normal skip_test
```Contents of /etc/X11/xorg.conf:
```
Section "Device"
    Identifier    "Internal Video"
    Driver        "vesa"
#    Driver        "intel"
#    Option        "AccellMethod"        "exa"
#    Option        "ExaNoComposite"    "true"
#    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Touch Screen Display"
EndSection

Section "InputDevice"
    Identifier    "External Mouse"
    Driver        "mouse"
    Option        "SendCoreEvents"    "true"
EndSection

Section "InputDevice"
    Identifier    "Touch Screen"
    Driver        "fpit"
    Option        "Device"        "/dev/ttyS0"
    Option        "AlwaysCore"        "on"
    Option        "BaudRate"        "19200"
    Option        "MaximumXPosition"    "10240"
    Option        "MaximumYPosition"    "7680"
    Option        "MinimumXPosition"    "0"
    Option        "MinimumYPosition"    "0"
    Option        "InvertY"
    Option        "Passive"
    Option        "TrackRandR"
    Option        "CorePointer"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Touch Screen Display"
    Device        "Internal Video"
    SubSection    "Display"
        Depth    24
        Modes    "1024x768" "800x600"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Touch Screen"
    InputDevice    "External Mouse"
EndSection

```Ignore the fact that I'm using the vesa driver for now if it's not relevant to the touch screen issue.  The Xorg driver for this machine's Intel 830MG is broken as hell, and vesa works just fine for now.

Help?

---

