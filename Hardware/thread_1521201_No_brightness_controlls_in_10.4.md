---
title: "No brightness controlls in 10.4?"
date: 2010-06-30
forum: Hardware
---

### Post by zackhawkins0103 on 2010-06-30
I recently downloaded Ubuntu Lucid Lynx in hopes it would make my computer faster, and it did. The only thing that is wrong is when I try to set the brightness to a different level it automatically keeps it at 100% no matter what I try and do.

here is information on my hardware:

zack@zack-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

I would really like to get this error with my graphics card fixed, I believe this is the graphics card:

zack@zack-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

or

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by sanderd17 on 2010-06-30
How are you trying to lower the brightness? with the FN+F6 and FN+F7 keys? Maybe you can try compiz (ccsm) to do this.

---

### Post by zackhawkins0103 on 2010-06-30
no by using system-> preferences -> power management -> the slide bar

---

### Post by yahmorah25 on 2010-06-30
on my acer i have the brightening keys as the left and right arrow keys so see if you might have the same thing that might work pressing the fn left or right key

---

### Post by zackhawkins0103 on 2010-06-30
[LEFT]its a toshiba sattalite a105 s4001 and no those keys didnt work :(
[/LEFT]

---

### Post by anachoret on 2010-08-12
HP Mini 1030NR (vga controller - 945GME, display controller - 945GM/GMS/GME)


The initial brightness is 100%, BIOS has no any display's settings.

The level of the brightness has not saves.

The functional control's keys (Fn+F3/F4) are working fine, the brightness goes down as well as up. When I switch to the battery the brightness dims but since I have plugged the AC adapter back the brightness comes to 100%.

/proc/acpi/video/IGD/LCD

May be this path is responsible for the absence the brightnes' control in "Power Management" window.

Any idea how to resolve this annoyance?

---

### Post by ngrieb on 2010-08-30
I cannot get anything to work with my Toshiba NB305 either... it is in the same graphics card family. I tried compiz and got no results: sliding bars of any sort around does nothing. This problem seems pretty large...

---

### Post by anachoret on 2010-08-31
Here it is my workaround after a research of couple forums.

1. add i915.modeset=0 acpi_backlight=vendor into grub.cfg as a kernel parameter
2. add /usr/bin/setpci -s 00:02.0 F4.B=30 into /etc/rc.local (changes the display's brightnes: 30 - brigthness value, 00:02.0 - id of the graphic adapter).
3. add the following command as a event's script in laptop-mode package (restores the monitor's brightness after power restore when AC adapter plugen on):
/usr/bin/xrandr --output LVDS --set BACKLIGHT 66 BACKLIGHT_CONTROL legacy --output VGA --auto

At last, the brightness control in "Power management" windows has appear.

---

