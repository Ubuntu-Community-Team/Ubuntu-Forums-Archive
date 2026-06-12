---
title: "No hardware drivers after upgrade"
date: 2010-08-22
forum: Hardware
---

### Post by Despot Despondency on 2010-08-22
Hi,

I just performed a routine upgrade on my system and when I rebooted it was low graphics mode. I went to System -> Administration -> Hardware Drivers to reinstall the drivers for my graphics card and there are now no propriety drivers on my system. 

Has anyone else had this problem? Any ideas what I should do?

I forgot to mention that my graphics card is an

Intel Corporation 82Q35 Express Integrated Graphics Controller

---

### Post by Despot Despondency on 2010-08-23
Bump.

---

### Post by Fafler on 2010-08-23
The Intel chips doesn't need 3rd. party drivers, so the problems must be somewhere else.

Try upgrading again from the terminal. sudo apt-get update and sudo apt-get upgrade and look for any errors.

---

### Post by Despot Despondency on 2010-08-23
Hi, thanks for the response. 

I've tried sudo apt-get update and sudo apt-get upgrade and no errors show up. 

Here's my output from lspci

```

00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)
06:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)

```

---

### Post by Despot Despondency on 2010-08-23
OK, well I've installed a new version of ubuntu on my computer and there are now more options on the screen resolution. 

I'm now up to 1024x768, which is slightly better than before, but it still looks like I'm in the 80's.

I think I need to configure X myself for which I need the console login. How do I get to the console login on ubutnu? I only seem to be able to get various GUI's.

---

### Post by Despot Despondency on 2010-08-23
OK, 

I've reconfigures my xorg.conf file, but that didn't seem to help much.

I found the post [http://ubuntuforums.org/showthread.php?t=1370258&highlight=monitor+unknown]("http://ubuntuforums.org/showthread.php?t=1370258&highlight=monitor+unknown") which works. However, it is a bit of a fiddle and more of a work around than a solution to the real problem.

When I go to system -> preferences -> monitors it says that the monitor is unknown. This is strange and I think the source of the problem.

I have the monitor model in my xorg.conf, so I don't know it is registered as unknown. 

Any suggestions on how to get a monitor detected in Ubuntu?

Here's my xorg.conf for reference

```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Default Screen" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "dri"
        Load  "dri2"
        Load  "record"
        Load  "dbe"
        Load  "extmod"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        Identifier   "Default Monitor"
        VendorName   "ViewSonic"
        ModelName    "VA1916w"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "CacheLines"                # <i>
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "DRI"                       # [<bool>]
        #Option     "NoDDC"                     # [<bool>]
        #Option     "ShowCache"                 # [<bool>]
        #Option     "XvMCSurfaces"              # <i>
        #Option     "PageFlip"                  # [<bool>]
        Identifier  "Default Graphics Card"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "82Q35 Express Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Default Graphics Card"
        Monitor    "Default Monitor"
        SubSection "Display"
                Viewport   0 0
                Depth     24
                modes     "1440x900"
        EndSubSection
EndSection

```

---

