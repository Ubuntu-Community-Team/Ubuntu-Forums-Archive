---
title: "Brightness Fn keys sometimes work, sometimes don't"
date: 2015-03-20
forum: Hardware
---

### Post by Keith_Helms on 2015-03-20
I'm running Xubuntu 14.04 on the latest kernel (3.13.0-48) and am up to date on all maintenance.  On my Sager laptop, the brightness down and up keys are Fn-F8 and Fn-F9.  After some boots, the keys will work.   After others, they don't work at all.   I installed the xfce4-brightness-plugin applet on the taskbar and that always seems to work, whether the hotkeys do or not.   Other hotkeys, such as Fn-F5 and Fn-F6 to adjust the volume always work.

My system has Nvidia Optimus graphics and I'm currently using Nvidia Prime and running under the nvidia-331 graphics driver.  Under /sys/class/backlight I see only "intel_backlight".  I can adjust the brightness by changing to that directory and echoing a value into the brightness file.

 So far, I've tried half a dozen things from various postings.

I added **acpi_osi=Linux acpi_backlight=vendor video.use_native_backlight=1** to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub (yes I did an update-grub afterwards)

I added the following to /usr/share/X11/xorg.conf.d

Created 20-intel.conf containing
```
Section "Device"
        Identifier  "card2"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```

Created 80-backlight.conf containing
```
Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "sna"
    Option "Backlight" "intel_backlight" # use your backlight that works here
    BusID "PCI:0:2:0"
EndSection

```

And finally, in /etc/X11/xorg.conf in the following section, I added the highlighted line
```
Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
   ** Option "RegistryDwords" "EnableBrightnessControl=1"**
EndSection
```

I tried the debugging steps listed in [https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

The command
```
xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'
```

Never returns anything, whether the keys are currently working or not.

**sudo evtest** never returns anything either.

If the keys are currently working, then acpi_listen DOES return
```
video/brightnessdown BRTDN 00000087 00000000
video/brightnessup BRTUP 00000086 00000000
```

At this point I'm at a loss on what else to try.

---

