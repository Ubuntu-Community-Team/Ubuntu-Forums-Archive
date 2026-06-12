---
title: "Acer 4810T hybrid graphics (Intel + ATI 4330) brightness issues"
date: 2013-10-23
forum: Hardware
---

### Post by RE6rFTA on 2013-10-23
Hi,

I have some problems with brightness settings in my notebook with Ubuntu 13.10. I switched off radeon card by using vgaswitcheroo, but Ubuntu still trying to set backlight using radeon driver. After checking /sys/class/backlight folder I get 3 folders: acer_wmi, intel_backlight and radeon_bl1. After adding acpi_backlight=vendor, changing brightness in ubuntu results changing values in acer_wmi/brightness, but brightness of the screen is not changing at all. After blacklisting acer_wmi, I get just intel_backlight and radeon_bl1 forlders, but changing the brighness in Ubuntu changes only values in radeon_bl1 folder. Using command like: ```
 echo 20000 > /sys/class/backlight/intel_backlight/brightness 
``` changes the brightness of screen, but I just want to configure it by using Ubuntu settings. I would be very gratful for help in solving a problem.

---

### Post by Toz on 2013-10-23
Hello and welcome to the forums.

Can you try creating the file **/usr/share/X11/xorg.conf.d/20-intel.conf**:
```
sudo -i gedit /usr/share/X11/xorg.conf.d/20-intel.conf
```
...with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...and logging out and back in again to test?

If it doesn't work, can you post back:
```
lspci -k | grep -iA3 VGA
```
and your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by RE6rFTA on 2013-10-23
It works great now when I'm using Ubuntu Settings to change the brightness, but using function keys in my notebook causing grafical shell's freeze. I guess changing brightness in this way still using wrong file or smth... Hard to check it if my sytem freeze after changing it.

---

### Post by Toz on 2013-10-23
Can I see a listing of your currently running modules:
```
lsmod
```
...and a copy of your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated

...and your Xorg.0.log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

