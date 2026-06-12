---
title: "HDMI no longer works after booting/updating windows twice"
date: 2018-02-07
forum: Hardware
---

### Post by explodymatt on 2018-02-07
Specs:
Ubuntu 17.10 with xfce4 installed via apt
Dell Latitude 7567
CPU i5 7300HQ
Nvidia 1050Ti with binary blob from nvidia


Dual boot to Windows 10


I booted (and updated) windows for the first time in a while (first time since spectre).


Now when I plug in hdmi on the switchable graphics, the monitor will not turn on. The event triggers xfce to open the display dialog though.


Xrandr output:
```


    eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
       1920x1080     60.02*+  59.93    48.03
       1680x1050     59.95    59.88
       1600x1024     60.17
       1400x1050     59.98
       1280x1024     60.02
       1440x900      59.89
       1280x960      60.00
       1360x768      59.80    59.96
       1152x864      60.00
       1024x768      60.04    60.00
       960x720       60.00
       928x696       60.05
       896x672       60.01
       960x600       60.00
       960x540       59.99
       800x600       60.00    60.32    56.25
       840x525       60.01    59.88
       800x512       60.17
       700x525       59.98
       640x512       60.02
       720x450       59.89
       640x480       60.00    59.94
       680x384       59.80    59.96
       576x432       60.06
       512x384       60.00
       400x300       60.32    56.34
       320x240       60.05
    DP-1 disconnected (normal left inverted right x axis y axis)



```Don't see anything happen on DMESG


This does not change when plugging in HDMI.


If I use prime-select to switch to the nvidia card it works.


Display of any windows native widgets when I booted windows is also extremely sluggish (taking 10s to display menus etc) but some software works fine.


I was previously having trouble with gnome on wayland (poor battery life, needing to reboot to use prime-select rather than just restarting X/gdm). Attempting to use it rather than xfce now to see if it is something to do with xfce leads to a logon screen loop. This could be a separate issue.
Disabling wayland makes gnome work again, but it does not react in any way to plugging in hdmi.




edit: sudo lshw -c output
```


      *-display
           description: VGA compatible controller
           product: Intel Corporation
           vendor: Intel Corporation
           physical id: 2
           bus info: pci@0000:00:02.0
           version: 04
           width: 64 bits
           clock: 33MHz
           capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
           configuration: driver=i915 latency=0
           resources: irq:126 memory:dd000000-ddffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff



```    
manually trying to enable/force 1920x1080 for DP-1 leads to 
```
    xrandr: Configure crtc 1 failed

```


Seems to be timed about right for this issue:

[https://answers.microsoft.com/en-us/windows/forum/windows_10-performance/intel-nvidia-laptop-freeze-problem/93e7004a-62b1-4211-8e37-4c136608865e?auth=1](https://answers.microsoft.com/en-us/windows/forum/windows_10-performance/intel-nvidia-laptop-freeze-problem/93e7004a-62b1-4211-8e37-4c136608865e?auth=1)

This  seems consistent with the fact that the intel driver now only detects  the built in screen and the nvidia driver only detects the external  screen on windows.

Anyone know if there is a bios setting that this update might have changed and how I can set it back?

---

