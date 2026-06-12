---
title: "Bizarre Boot-up Freeze Caused by Mouse"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by snl2587 on 2007-11-05
I came across a strange boot-up problem the other day with Gutsy: Whenever I boot-up my laptop with my M$ Basic Optical (Wired,USB) Mouse attached, the computer will freeze indefinitely with the Ubuntu load bar stuck at about 25%. If I disconnect the mouse for the purpose of booting, the computer boots fine (which was really frustrating when I was trying to figure this out, since I personally never think about attached), and I can reconnect it later in Gutsy and it works fine.

Is there some kind of error log that would be useful to diagnose this issue? I'm sure there's a simple fix (like ignoring the mouse temporarily).

---

### Post by ROBarber on 2007-11-06
Hi.

First of all on a terminal please type:

cat /proc/bus/input/devices (with sudo if you are not a root)

and

nano /etc/X11/xorg.conf

ans please paste the text here.

regards

---

### Post by snl2587 on 2007-11-06
Thanks for getting back to me. Here is the output from the input devices list:

```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=1004 2200002 3802078 f950d401 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0004 Version=0000
N: Name="Sleep Button (FF)"
P: Phys=button_sleep/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=event6 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0003 Vendor=045e Product=0084 Version=0110
N: Name="Microsoft Basic Optical Mouse"
P: Phys=usb-0000:00:13.1-2/input0
S: Sysfs=/class/input/input8
U: Uniq=
H: Handlers=mouse2 event8 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

And here is the other thing:

```

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
        Driver          "fglrx"
        Busid           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
Section "Extensions"
        Option          "Composite"     "1"
EndSection

```

Thanks again!

---

### Post by ROBarber on 2007-11-06
ok, try to modify the following line

Option          "Protocol"      "ImPS/2"

replacing ImPS/2 with auto. this is a standard protocol used in OS.

after rebooting if u are unable to use your mouse, use Alt+F2 keys combination, and with Tab and Enter, try to reach 'Show list of known application' option and open a commnad terminal to modify the xorg.conf file to the previous state.
good luck

---

### Post by snl2587 on 2007-11-06
I tried changing that line to no avail. If anyone has any other ideas they would be appreciated.

---

### Post by snl2587 on 2007-11-09
I still can't figure this out. Does anyone know how to fix this?

---

### Post by stoto on 2008-02-27
I got the same boot up fault. It doesnt even boots the kernel. After grub it says:
kernel alive
kernel direct mapping tables....freezes

If i plug out my usb mouse and restart, then is works fine.
i can plug in the mouse when the system is booted and then mouse works, no freeze.
However i cant boot up with the mouse plugged in.

---

