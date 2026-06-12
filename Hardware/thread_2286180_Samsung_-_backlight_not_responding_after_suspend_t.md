---
title: "Samsung - backlight not responding after suspend to ram"
date: 2015-07-10
forum: Hardware
---

### Post by e-San on 2015-07-10
Hi!


After upgrading kernel to 4.x (4.1.1-040101-generic) i can not control brightness.
After adding 
```
video.use_native_backlight=1
```
or 
```
acpi=vendor
```
I am able to control brightness with Fn+F2/F3.


But after suspending to ram hotkeys stop work.


After making some small research i've found:
```
ls /sys/class/backlight/
radeon_bl0/ samsung/
```


And commands do affect brightness:
```
# echo 2 > /sys/class/backlight/samsung/brightness 
# echo 50 > /sys/class/backlight/radeon_bl0/brightness
```


But after waking my laptop first one (samsung) stops working.


How can i solve this problem?


```
# uname -a
Linux sammie-mint 4.1.1-040101-generic #201507030635 SMP Fri Jul 3 10:38:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


# lspci | grep -i vga
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7400G]


#dmesg | grep -i backlight
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.1.1-040101-generic root=UUID=90e7021f-c052-4211-ab4b-62e11262ac29 ro quiet splash ath9k.ps_enable=1 acpi_backlight=vendor vt.handoff=7
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.1.1-040101-generic root=UUID=90e7021f-c052-4211-ab4b-62e11262ac29 ro quiet splash ath9k.ps_enable=1 acpi_backlight=vendor vt.handoff=7
[    1.794176] [drm] radeon atom DIG backlight initialized
```


According to [https://wiki.ubuntu.com/Kernel/Debugging/Backlight#Intel_HD_Graphic_Controllers](https://wiki.ubuntu.com/Kernel/Debugging/Backlight#Intel_HD_Graphic_Controllers)
I made config file:
```
cat /usr/share/X11/xorg.conf.d/80-backlight.conf
Section "Device"
    Identifier  "Radeon Graphics"
    Driver      "radeon"
    Option      "Backlight"       "radeon_bl0" # use your backlight that works here
EndSection
```
  
But it won't help.

---

### Post by e-San on 2015-07-20
bump

---

