---
title: "Graphire 2 problems with Ubuntu 5.10"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by lisux on 2005-10-26
Hi all.
I have used the linux wacom drivers with my graphire 2 tablet in the past for red hat 9 and debian 3 without problems.
Now i am using Ubuntu 5.10 but is impossible for me to get the tablet work properly.
Using the dafaults modules and drivers that came with ubuntu sometimes i can  reach some parts of the screen, i am using the tablet and then i can go to the top, the pencil stops some pixels before, or to the right side of the screen and so on ...
I have to put the pencil far from the tablet and wait for 4 or 10 seconds then the pencil works correctly again.
I think that is a kernel modules problems so i tried to compile the ubuntu kernel sources using the linux wacom sources for 2.6.9, but ubuntu uses a 2.6.12 kernel and i get some error cwhile compiling:
  CHK     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
make[1]: `arch/i386/kernel/asm-offsets.s' is up to date.
  CHK     include/linux/compile.h
  CHK     usr/initramfs_list
  CC [M]  drivers/usb/input/hid-core.o
drivers/usb/input/hid-core.c:1537: error: `HID_QUIRK_2WHEEL_MOUSE_HACK
_BACK' undeclared here (not in a function)
drivers/usb/input/hid-core.c:1537: error: initializer element is not constant
drivers/usb/input/hid-core.c:1537: error: (near initialization for `hid_blacklist[63].quirks')
drivers/usb/input/hid-core.c:1537: error: initializer element is not constant
drivers/usb/input/hid-core.c:1537: error: (near initialization for `hid_blacklist[63]')
drivers/usb/input/hid-core.c:1538: error: `HID_QUIRK_2WHEEL_MOUSE_HACK_EXTRA' undeclared here (not in a function)
drivers/usb/input/hid- core.c:1538: error: initializer element is not constant
drivers/usb/input/hid-core.c:1538: error: (near initialization for `hid_blacklist[64].quirks')
drivers/usb/input/hid-core.c:1538: error: initializer element is not constant
drivers/usb/input/hid-core.c:1538: error: (near initialization for `hid_blacklist[64]')
drivers/usb/input/hid-core.c:1540: error: initializer element is not constant
drivers/usb/input/hid-core.c:1540: error: (near initialization for `hid_blacklist[65]')
drivers/usb/input/hid-core.c:1541: error: initializer element is not constant
drivers/usb/input/hid-core.c:1541: error: (near initialization for `hid_blacklist[66]')
drivers/usb/input/hid-core.c:1542: error: initializer element is not constant
drivers/usb/input/hid-core.c:1542: error: (near initialization for `hid_blacklist[67]')
drivers/usb/input/hid-core.c:1543: error: initializer element is not constant
drivers/usb/input/hid-core.c:1543: error: (near initialization for `hid_blacklist[68]')
drivers/usb/input/hid-core.c:1544: error: initializer element is not constant
drivers/usb/input/hid-core.c:1544: error: (near initialization for `hid_blacklist[69]')
drivers/usb/input/hid-core.c:1545: error: initializer element is not constant
drivers/usb/input/hid-core.c:1545: error: (near initialization for `hid_blacklist[70]')
drivers/usb/input/hid-core.c:1546: error: initializer element is not constant
drivers/usb/input/hid-core.c:1546: error: (near initialization for `hid_blacklist[71]')
drivers/usb/input/hid-core.c:1547: error: initializer element is not constant
drivers/usb/input/hid-core.c:1547: error: (near initialization for `hid_blacklist[72]')
drivers/usb/input/hid-core.c:1549: error: initializer element is not constant
drivers/usb/input/hid-core.c:1549: error: (near initialization for `hid_blacklist[73]')
make[3]: *** [drivers/usb/input/hid-core.o] Error 1
make[2]: *** [drivers/usb/input] Error 2
make[1]: *** [drivers/usb] Error 2
make: *** [drivers] Error 2

My wacom and server sections for my xorg.conf file are:
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"   # USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"   # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"   # USB ONLY
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection
.....

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"      "CoreKeyboard"
        InputDevice     "Configured Mouse"      "SendCoreEvents"
        InputDevice     "stylus"                "CorePointer"
        InputDevice     "eraser"                "CorePointer"
        InputDevice     "cursor"                "CorePointer"
EndSection


Has anybody have similar problems, or anybody are using a graphire 2 with Ubuntu 5.10?
Thanks

---

### Post by williamx on 2006-01-11
I have a Graphire 2 with the exact same problems.. I also cant get the double-click part of the side-button to work as doubleclick.. It`s just rightclick..

Have You solved this problem yet? In that case, how?

---

