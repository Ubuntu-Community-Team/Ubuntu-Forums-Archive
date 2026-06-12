---
title: "[SOLVED] Sound/Audio Problem - Intel HDA on a Gateway P-6831FX"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by th3t1nm4n on 2008-01-23
Hello, I purchased a Gateway P-6831FX the other day, wiped the HDD of Vista, and installed Ubuntu Gutsy (7.10)

I already installed the latest nvidia binary drivers and fixed the resolution, so right now I'm working on audio.

Right now I can only get audio out of the headphone jack, I don't get any sound out of the built-in speakers. I know that this laptop is fresh on the shelves, but I was wondering if anyone has a solution for my problem.

So far I've tried upgrading to the latest version of ALSA as detailed here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
That didn't work.

Then I read on the forums that people with a similar card got it to work by re-installing Ubuntu after upgrading to the latest ALSO so it wouldn't conflict with this, and then installing linux-backports-modules-generic
I tried that and it didn't work either.

Then I tried adding each of these to my /etc/modprobe.d/alsa-base one at a time and rebooting, but none of them worked.
options snd-hda-intel
options snd-hda-intel model=lenovo
options snd-hda-intel model=acer

Without those, when I have audio coming out of the headphone jack, alsamixer displays "Generic 111d ID 76b0" as my chip, but I haven't had any luck finding out what that means or what codec I should play around with to get it to work out of my built-in speakers.

```
tinman@DebaserFX:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Generic 11c1 Si3054
Codec: Generic 111d ID 76b0

```

```
tinman@DebaserFX:~$  lspci -n | grep `lspci | grep -i audio | awk '{print $1}'` 
00:1b.0 0403: 8086:284b (rev 03)

```

```
tinman@DebaserFX:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: cc000000-ceffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: [88] Subsystem: Gateway 2000 Unknown device 0690
        Capabilities: [80] Power Management version 3
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f4604800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f4600000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: f4000000-f40fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0690
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f4100000-f41fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0690
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f4200000-f42fffff
        Prefetchable memory behind bridge: 00000000c2000000-00000000c20fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0690
        Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0690
        Capabilities: [a0] Power Management version 2

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: f2000000-f3ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0690
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at f4604c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=32
        Memory behind bridge: f4300000-f43fffff
        Capabilities: [50] Subsystem: Gateway 2000 Unknown device 0690

00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at 18d8 [size=8]
        I/O ports at 18cc [size=4]
        I/O ports at 18d0 [size=8]
        I/O ports at 18c8 [size=4]
        I/O ports at 18e0 [size=32]
        Memory at f4604000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable-
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: medium devsel, IRQ 10
        Memory at c2100000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0609 (rev a2) (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1100
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint IRQ 0

03:00.0 Mass storage controller: Silicon Image, Inc. Unknown device 3531 (rev 01)
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f4102000 (64-bit, non-prefetchable) [size=128]
        Memory at f4100000 (64-bit, non-prefetchable) [size=8K]
        I/O ports at 3000 [size=128]
        Capabilities: [54] Power Management version 2
        Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Legacy Endpoint IRQ 0

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at 4000 [size=256]
        Memory at f4200000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at c2000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

0c:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI])
        Subsystem: Agere Systems FW323
        Flags: bus master, fast Back2Back, medium devsel, latency 96, IRQ 16
        Memory at f4300000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

```

For now I'm stuck on external speakers at home and headphones while mobile.

[---Edit--]
I just looked it up on the Gateway website and the audio chip appears to be a SigmaTel 92HD71B Dual SPDF, so I'm going to dig into that.

[--Edit--]
I found the chip on the manufacturer's website here: [http://www.idt.com/?catID=18442401](http://www.idt.com/?catID=18442401)
According to Wikipedia "Sigmatel sold its computer audio business in mid 2006 to Integrated Device Technology, Inc."
So right now I'm contacting them about support, still got nothing out of the built-in speakers.

---

### Post by psavach on 2008-01-31
I know that this is kind of off-topic but it seems you might be the best person to ask.  I purchased this same laptop yesterday and am working on getting Gutsy installed.  When I boot from cd before it goes into live mode I get the starting in safe graphics mode message and after I continue it goes back to the text log and freezes completely.  Do you happen to have any tips here?

---

### Post by Yellow Pasque on 2008-02-01
Side note: I see a lot of unknown devices in your lspci output. Try running the following to get the latest PCI database info:
```
sudo update-pciids
```

---

### Post by th3t1nm4n on 2008-02-01
Hi, it's nice to see another person experimenting with Linux on this laptop :]

At the boot menu I selected the "safe graphics" mode because I had this problem too, after using that I was able to install Ubuntu fine. I installed again because I wanted to move to the xfce desktop (I like it more than Gnome on laptops), so I installed Xubuntu and that worked fine this way too.

On this laptop you will want to use the official nvidia binary drivers that aren't in the repositories (ubuntu software update stream) yet, to do so follow the first paragraph on this page:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

To get the native 1440x900 resolution you'll want to reed this:
[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541)

Here is my current xorg.conf as an example of it modified:
> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Jan 11 15:05:59 PST 2008

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
[COLOR="Red"]        Modes      "1440x900" "1280x1024" "800x600"[/COLOR]
    EndSubSection
EndSection



---

### Post by th3t1nm4n on 2008-02-01
> **Temüjin said:**
> Side note: I see a lot of unknown devices in your lspci output. Try running the following to get the latest PCI database info:
```
sudo update-pciids
```

```
tinman@GodzillaFX:~$ sudo update-pciids
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  126k  100  126k    0     0   175k      0 --:--:-- --:--:-- --:--:--  233k
Done.
tinman@GodzillaFX:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: cc000000-ceffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: [88] Subsystem: Gateway 2000 Unknown device 0690
        Capabilities: [80] Power Management version 3
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f4604800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f4600000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: f4000000-f40fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0690
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f4100000-f41fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0690
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f4200000-f42fffff
        Prefetchable memory behind bridge: 00000000c2000000-00000000c20fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0690
        Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0690
        Capabilities: [a0] Power Management version 2

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: f2000000-f3ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0690
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at f4604c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=32
        Memory behind bridge: f4300000-f43fffff
        Capabilities: [50] Subsystem: Gateway 2000 Unknown device 0690

00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at 18d8 [size=8]
        I/O ports at 18cc [size=4]
        I/O ports at 18d0 [size=8]
        I/O ports at 18c8 [size=4]
        I/O ports at 18e0 [size=32]
        Memory at f4604000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable-
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: medium devsel, IRQ 10
        Memory at c2100000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800M GTS (rev a2) (prog-if 00 [VGA controller])
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1100
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint IRQ 0

03:00.0 Mass storage controller: Silicon Image, Inc. Unknown device 3531 (rev 01)
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f4102000 (64-bit, non-prefetchable) [size=128]
        Memory at f4100000 (64-bit, non-prefetchable) [size=8K]
        I/O ports at 3000 [size=128]
        Capabilities: [54] Power Management version 2
        Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Legacy Endpoint IRQ 0

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Gateway 2000 Unknown device 0690
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at 4000 [size=256]
        Memory at f4200000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at c2000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

0c:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI])
        Subsystem: Agere Systems FW323
        Flags: bus master, fast Back2Back, medium devsel, latency 96, IRQ 16
        Memory at f4300000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

tinman@GodzillaFX:~$ 

```

I think I tried that before, but I'm not sure. This laptop is brand new (hit the shelves earlier this month I think) so I suspect that a lot of the hardware on it isn't in that database yet.

---

### Post by th3t1nm4n on 2008-02-05
A reply from Sigmatel:
> It is an EOL product from Sigmatel, sorry that we do not have new development to support this product further.

Not very helpful to me though xD

---

### Post by psavach on 2008-02-10
so I finally got everything with the video worked out and i've noticed a couple of things.  I'm having the exact same audio issue as you (I'm assuming that you still haven't got this one resolved).

The other issue I'm having right now and I'm not sure what log I would find this in.  What's happening is on boot before the gui starts to load I'm getting an error about not being able to load specific memory or something along those lines.  Did/does this happen to you at all?

---

### Post by th3t1nm4n on 2008-02-23
Nope, I haven't had that problem at all. I'm not sure where it would log either, but possibly doing a dmesg would show it? I'm not sure.

My audio problem remains unsolved, for now I'm using external speakers and headphones.

---

### Post by th3t1nm4n on 2008-02-29
I just installed Hardy Heron Alpha 5 and I have audio working!
[https://wiki.ubuntu.com/HardyHeron/Alpha5](https://wiki.ubuntu.com/HardyHeron/Alpha5)

:D

New output:
```
tinman@GodzillaFX:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Generic 11c1 ID 1040
Codec: IDT 92HD71B8X

```

I found that the codec was added here: [http://www.kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.24-rc6/2.6.24-rc6-mm1/broken-out/git-alsa.patch](http://www.kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.24-rc6/2.6.24-rc6-mm1/broken-out/git-alsa.patch)

---

### Post by th3t1nm4n on 2008-03-07
Upgraded to Hardy Heron Alpha 6, sound is still working fine :)

---

