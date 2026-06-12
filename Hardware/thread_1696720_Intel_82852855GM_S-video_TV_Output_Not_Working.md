---
title: "Intel 82852/855GM S-video TV Output Not Working"
date: 2011-02-27
forum: Hardware
---

### Post by drewski3420 on 2011-02-27
Help! I'm running Xubuntu 10.10 (Xfce 4.6.2) on a Thinkpad R51 with onboard Intel graphics. I'm basically trying to set this up as a HTPC with XBMC to using in the living room. I've finally got everything working, except I still can't get the S-video output to work.

I've searched all over and found a few tips/workarounds, but nothing has helped.

If I startup with the S-video cable connected, the TV flashes white once, briefly, at the POST screen, but nothing else.

Here is the relevant part of lspci:

```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```My xorg.conf file looks like this (most of it was copied to cope with the error explained here: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)). I have to use the intel driver, otherwise Hardware Acceleration/OpenGL get disabled and no-go on XBMC.

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
    Option        "monitor-VGA"    "VGA"
    Option        "monitor-TV"    "TV"
    Option        "monitor-LVCD"    "LVCD"
    Option        "monitor-Svideo"    "S-Video
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section    "Monitor"
    Identifier    "VGA"
    Option "Ignore"    "true"
EndSection

Section "Monitor"
    Identifier    "LVCD"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier    "TV"
    Option    "Ignore"    "false"
EndSection

Section "Monitor"
    Identifier    "S-Video"
    Option    "Ignore"    "false"
EndSection

```When i view xrandr, it shows the laptop display and the VGA port, but not TV out or S-video I've verified the VGA port works with this config just by plugging it in (I'm viewing a cloned desktop on a CRT monitor right now).

```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 306mm x 230mm
   1024x768       85.0 +   75.1     70.1*    60.0  
   1280x1024      60.0  
   800x600        85.1     75.0     60.3  
   640x480        85.0     75.0     60.0  
   720x400        70.1  
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   85.0     75.0     70.1     60.0* 
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
```I don't need extended desktop, or anything like that. I just want to view the screen on a TV so I can leave the laptop on a shelf closed.

Does anyone have any tips or ideas on what I can do to get S-video output working on my machine? If more info is needed, I'd be happy to provide to get my problem resolved.

Thanks.

---

### Post by mailsub2000 on 2011-07-29
i810 drivers works for s-video. somehow i810 drivers dont work well with recent kernels. dont know what modifications they need.
how about using vga to s-video converter and do vga out.
p.s. vga to s-video cable may not work in some cases you will
need converter only.

---

### Post by realzippy on 2011-07-29
You could check if it is intel/kernel related.
Disable the xorg.conf (or choose "vesa" instead of "intel" ),
then check 
*xrandr -q* again....

---

