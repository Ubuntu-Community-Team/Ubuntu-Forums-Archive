---
title: "Problems with screen resolution and graphics drivers on dell inspiron 1564"
date: 2010-04-19
forum: Hardware
---

### Post by HeyOutThere on 2010-04-19
hi, relatively new to Ubuntu having used it on my PC for maybe two months now, recently installed 9.10 to my dell inspiron 1564 laptop and i am having issues with the screen resolution.

Ubuntu does not detect the display (1024x576) and the only available resolutions are 800x600 and 1024X768 resulting in a stretched screen and distortion.

i have tried to add a new resolution using xrandr using [http://http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html ]("http://http//www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")but after entering "xrandr --output" i get an error that reads "could not set configuration for CRTC 256"

lspci yields:

```
00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Arrandale Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)
```

Help please?

---

### Post by HeyOutThere on 2010-04-19
spent several hours fiddling, tried this-
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html#more-3469](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html#more-3469)
without success.

asking again for help, hello?

---

### Post by HeyOutThere on 2010-04-25
I've been struggling with this issue for about a week, anyone?

---

### Post by dino99 on 2010-04-25
can you talk a little about hardware (graphic chip) and distro installed

first into console, run: sudo dpkg-reconfigure xserver-xorg

then goto system admin hardware-driver and see if your driver is activated

---

### Post by HeyOutThere on 2010-04-25
even after running sudo dpkg-reconfigure xserver-xorg the only driver showing up in hardware drivers is for the wireless card.

the graphics card, i am assuming, is whatever comes with the i3 processor
which is, as far as i can tell, the  "intel corporation arrandale integrated graphics controller (rev12)"
or, according to sysinfo, there is something called "intel corporation 5 series/3400 series chipset"

---

### Post by HeyOutThere on 2010-04-25
not sure if this is related (or even what/how to use this information) but this is the contents of my xorg.conf file
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

---

### Post by Joe on 2010-04-25
What kernel are you running?  I think the new Intel graphics chip requires the most recent kernel (the default kernel on Lucid).

Check out this thread: [http://ubuntuforums.org/showthread.php?t=1395454&page=3](http://ubuntuforums.org/showthread.php?t=1395454&page=3)

---

### Post by HeyOutThere on 2010-04-25
the kernal is 2.6.31-14-generic

---

### Post by Joe on 2010-04-25
> **HeyOutThere said:**
> the kernal is 2.6.31-14-generic

You can try upgrading to 2.6.32 if you haven't yet or install the Lucid RC (or wait for the final Lucid release in a few days).

---

### Post by HeyOutThere on 2010-04-26
updating to lucid did the trick,
thanks a million!

---

