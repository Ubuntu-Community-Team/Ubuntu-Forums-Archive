---
title: "Ubuntu 13.04 / Sabrent USB-2011 (Displink Adapter DL-195) / XORG.CONF"
date: 2013-10-12
forum: Hardware
---

### Post by tfkennady on 2013-10-12
Hey!

I'd really appreciate it if someone could help me configure my xorg.conf so that I can use my displaylink adapter for a 3rd monitor. I've tried many variations and I know that I'm close but can't quite find the right mix to make it all work. I've done a lot of reading on this and feel that I have most of the prerequisites in place for the xorg.conf file to be edited correctly.  

I have the "green screen of success" and if the adapter is plugged in during boot up the Ubuntu loading screen displays on the third monitor temporarily, on shutdown I have scrolling text on that screen as well. Additionally from the login screen I can ctr+alt+F1 and run a shell on the displaylink screen. This also works when booting into recovery. Once logged in the displaylink adapter screen freezes with the previous image. I know that it means that linux is recognizing the device.

Sorry for the lengthy post but I wanted to be as thorough as possible.

**Current Setup -** 
Comp: Asus G71GX / Ubuntu 13.04 with an additional 22" Sceptre monitor connected via VGA
Video Card: Nvidia GeForce GTX 260M w/nvidia-304 drivers. I have the 310, 313, 325 & 331 drivers available as well. 
Kernel: 3.10

**blacklist-framebuffer.conf**
I've also added blacklist udl and have tried both blacklist udlfb & #blacklist udlfb, none of which have worked for me.

**Edit /etc/gdm/Init/Default**
this file does not exsist for me so I can not add
gdmwhich () {
    ....
}
        
XRANDR=`gdmwhich xrandr`
if [ "x$XRANDR" != "x" ] ; then
    $XRANDR -o 0
fi

sysresources=/etc/X11/Xresources[B]

Current xorg.conf (what my xorg.conf is from installing nvidia drivers)[/B]
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

**THIS XORG.CONF BOOTED BUT MY 3RD DISPLAY DID NOT WORK**
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "DisplayLinkScreen"
    Screen      1  "Internal" RightOf "DisplayLinkScreen"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Monitor"
    Identifier     "DisplayLinkMonitor"
EndSection
Section "Device"
    Identifier  "DisplayLinkDevice"
    Driver    "fbdev"
    BusID       "USB"
    Option      "fbdev" "/dev/fb0"
EndSection
Section "Screen"
    Identifier      "DisplayLinkScreen"
    Device          "DisplayLinkDevice"
    Monitor         "DisplayLinkMonitor"
    SubSection "Display"
        Depth       24
        Modes       "1920x1200" "1920x1080" "1680x1050" "1600x1200" "1440x900" "1366x768" "1280x1024" "1280x960" "1280x800"  "1280x768"  "1152x864" "1024x768" "800x600" "640x480" 
    EndSubSection
EndSection

**LSUSB RETURNS**:
Bus 002 Device 002: ID 17e9:0360 DisplayLink 
Bus 002 Device 004: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**DMESG RETURNS**: 
 usb 2-3: new high-speed USB device number 2 using ehci-pci
[    1.375923] usb 2-3: New USB device found, idVendor=17e9, idProduct=0360
[    1.375986] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.376054] usb 2-3: Product: Sabrent USB-2011
[    1.376112] usb 2-3: Manufacturer: DisplayLink
[    1.376169] usb 2-3: SerialNumber: 660271
[    1.488014] tsc: Refined TSC clocksource calibration: 2526.999 MHz
[    1.488078] Switching to clocksource tsc
[    1.628012] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.667462] ata1.00: ATA-8: ST9500325AS, 0002SDM1, max UDMA/133
[    1.667522] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.669738] ata1.00: configured for UDMA/133
[    1.669905] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      0002 PQ

---

### Post by tfkennady on 2013-10-12
Can anyone confirm the depth settings?

16 vs 24

I've read that both should work but 24 is a lot of information to pass via USB 2.0

---

### Post by tfkennady on 2013-10-12
is Xinerama required in the Server Layout settings?

Option	    "Xinerama" "0" #Could not get this to work it has to be disable

---

### Post by tfkennady on 2013-10-12
Last one for today... this setting found here:

[https://wiki.archlinux.org/index.php/DisplayLink#Dual_X_setup](https://wiki.archlinux.org/index.php/DisplayLink#Dual_X_setup)

To automatically load udlfb at boot, create the file udlfb.conf in /etc/modules-load.d/ with the following contents: 
 /etc/modules-load.d/udlfb.conf

udlfb

---

### Post by tfkennady on 2013-10-13
Really need help with this.

Thanks in advance.

---

### Post by tfkennady on 2013-10-14
Bump

---

### Post by tfkennady on 2013-10-20
Please help

---

### Post by millhouse513 on 2013-11-16
I'm having similar issues.  I've got the Asus G51JX w/the USB-2k-a pluggable displaylink adapter.  I've blacklisted udl and if I plug it in, dmesg shows output like it's detected it but the only thing I can get is console output to it.

I'd really like to get two external monitors working with my laptop.

---

