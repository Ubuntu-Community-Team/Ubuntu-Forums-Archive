---
title: "Cannot switch external monitor to 60Hz after recent update"
date: 2020-06-01
forum: Hardware
---

### Post by aspz on 2020-06-01
I am running ubuntu 18.04 and I recently did a system update which installed the following packages (according to /var/log/apt/history.log):

```

 libdevmapper1.02.1:amd64 (2:1.02.145-4.1ubuntu3.18.04.2, 2:1.02.145-4.1ubuntu3.18.04.3), liblvm2cmd2.02:amd64 (2.02.176-4.1ubuntu3.18.04.2, 2.02.176-4.1ubuntu3.18.04.3), dmsetup:amd64 (2:1.02.145-4.1ubuntu3.18.04.2, 2:1.02.145-4.1ubuntu3.18.04.3), netplan.io:amd64 (0.99-0ubuntu3~18.04.1, 0.99-0ubuntu3~18.04.2), openssl:amd64 (1.1.1-1ubuntu2.1~18.04.5, 1.1.1-1ubuntu2.1~18.04.6), libsystemd0:amd64 (237-3ubuntu10.40, 237-3ubuntu10.41), libkmod2:amd64 (24-1ubuntu3.3, 24-1ubuntu3.4), python3-aptdaemon.gtk3widgets:amd64 (1.1.1+bzr982-0ubuntu19.2, 1.1.1+bzr982-0ubuntu19.3), libdevmapper-event1.02.1:amd64 (2:1.02.145-4.1ubuntu3.18.04.2, 2:1.02.145-4.1ubuntu3.18.04.3), dmeventd:amd64 (2:1.02.145-4.1ubuntu3.18.04.2, 2:1.02.145-4.1ubuntu3.18.04.3), lvm2:amd64 (2.02.176-4.1ubuntu3.18.04.2, 2.02.176-4.1ubuntu3.18.04.3), udev:amd64 (237-3ubuntu10.40, 237-3ubuntu10.41), kmod:amd64 (24-1ubuntu3.3, 24-1ubuntu3.4), libudev1:amd64 (237-3ubuntu10.40, 237-3ubuntu10.41), nplan:amd64 (0.99-0ubuntu3~18.04.1, 0.99-0ubuntu3~18.04.2), apport:amd64 (2.20.9-0ubuntu7.14, 2.20.9-0ubuntu7.15), python3-apport:amd64 (2.20.9-0ubuntu7.14, 2.20.9-0ubuntu7.15), libnss-myhostname:amd64 (237-3ubuntu10.40, 237-3ubuntu10.41), liblvm2app2.2:amd64 (2.02.176-4.1ubuntu3.18.04.2, 2.02.176-4.1ubuntu3.18.04.3), systemd-sysv:amd64 (237-3ubuntu10.40, 237-3ubuntu10.41), libpam-systemd:amd64 (237-3ubuntu10.40, 237-3ubuntu10.41), systemd:amd64 (237-3ubuntu10.40, 237-3ubuntu10.41), aptdaemon-data:amd64 (1.1.1+bzr982-0ubuntu19.2, 1.1.1+bzr982-0ubuntu19.3), libnss-systemd:amd64 (237-3ubuntu10.40, 237-3ubuntu10.41), libnetplan0:amd64 (0.99-0ubuntu3~18.04.1, 0.99-0ubuntu3~18.04.2), python3-aptdaemon:amd64 (1.1.1+bzr982-0ubuntu19.2, 1.1.1+bzr982-0ubuntu19.3), apport-gtk:amd64 (2.20.9-0ubuntu7.14, 2.20.9-0ubuntu7.15), aptdaemon:amd64 (1.1.1+bzr982-0ubuntu19.2, 1.1.1+bzr982-0ubuntu19.3), libssl1.1:amd64 (1.1.1-1ubuntu2.1~18.04.5, 1.1.1-1ubuntu2.1~18.04.6), libjson-c3:amd64 (0.12.1-1.3ubuntu0.2, 0.12.1-1.3ubuntu0.3), python3-problem-report:amd64 (2.20.9-0ubuntu7.14, 2.20.9-0ubuntu7.15)

```

Since this update, I am no longer able to run my LG 34UC99-W Ultrawide external monitor at 60Hz - it defaults to 30Hz which makes it pretty much unusable for anything productive. When I run xrandr, I see the following:

```

$ xrandr
Screen 0: minimum 320 x 200, current 3440 x 2520, maximum 8192 x 8192
eDP-1 connected primary 1920x1080+683+1440 (normal left inverted right x axis y axis) 293mm x 165mm
   3840x2160     60.00 +  59.98    59.97  
   3200x1800     59.96    59.94  
   2880x1620     59.96    59.97  
   2560x1600     59.99    59.97  
   2560x1440     59.99    59.99    59.96    59.95  
   2048x1536     60.00  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   2048x1152     59.99    59.98    59.90    59.91  
   1920x1200     59.88    59.95  
   1920x1080     60.01*   59.97    59.96    59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 connected 3440x1440+0+0 (normal left inverted right x axis y axis) 800mm x 335mm
   3440x1440     29.99* 
   2560x1080     60.00    59.94    50.00    60.00  
   1920x1080     60.00    60.00    50.00    59.94  
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024     60.02  
   1280x800      59.81  
   1152x864      59.97  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94
DP-2 disconnected (normal left inverted right x axis y axis)

```

My laptop's display is eDP-1 which despite being a 4K screen, I have set at a resolution of 1920x1080 (because who needs 4K on a 13" laptop?). My external monitor is DP-1. Notice how the only refresh rate for its native resolution is 29.99.

If I try to run:

```

$ xrandr --output DP-1 --mode 3440x1440 --rate 60

```

it has no effect.

I have noticed, however that when I unplug the display port monitor cable and then plug it back in that 60Hz is now listed as one of the available resolutions by xrandr:

```

$ xrandr
Screen 0: minimum 320 x 200, current 3440 x 2520, maximum 8192 x 8192
eDP-1 connected primary 1920x1080+683+1440 (normal left inverted right x axis y axis) 293mm x 165mm
   3840x2160     60.00 +  59.98    59.97  
   3200x1800     59.96    59.94  
   2880x1620     59.96    59.97  
   2560x1600     59.99    59.97  
   2560x1440     59.99    59.99    59.96    59.95  
   2048x1536     60.00  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   2048x1152     59.99    59.98    59.90    59.91  
   1920x1200     59.88    59.95  
   1920x1080     60.01*   59.97    59.96    59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 connected 3440x1440+0+0 (normal left inverted right x axis y axis) 800mm x 335mm
   3440x1440     59.97 +  49.99    29.99* 
   2560x1080     60.00    59.94    50.00    60.00  
   1920x1080     60.00    60.00    50.00    59.94  
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024     60.02  
   1280x800      59.81  
   1152x864      59.97  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
DP-2 disconnected (normal left inverted right x axis y axis)

```

Notice how the refresh rate 59.97 is suddenly available but unselected. If I try to select it by running either:

```

xrandr --output DP-1 --mode 3840x2160 --rate 60

```

or 

```

xrandr --output DP-1 --auto

```

it has no effect and the 60Hz option disappears from the list shown by xrandr.

My ~/.config/monitors.xml file looks like this:

```

<monitors version="2">
  <configuration>
    <logicalmonitor>
      <x>690</x>
      <y>1440</y>
      <scale>1</scale>
      <primary>yes</primary>
      <monitor>
        <monitorspec>
          <connector>eDP-1</connector>
          <vendor>AUO</vendor>
          <product>0x282b</product>
          <serial>0x00000000</serial>
        </monitorspec>
        <mode>
          <width>1920</width>
          <height>1080</height>
          <rate>120.01551055908203</rate>
        </mode>
      </monitor>
    </logicalmonitor>
    <logicalmonitor>
      <x>0</x>
      <y>0</y>
      <scale>1</scale>
      <monitor>
        <monitorspec>
          <connector>DP-1</connector>
          <vendor>GSM</vendor>
          <product>LG ULTRAWIDE</product>
          <serial>0x00064ebd</serial>
        </monitorspec>
        <mode>
          <width>3440</width>
          <height>1440</height>
          <rate>59.972618103027344</rate>
        </mode>
      </monitor>
    </logicalmonitor>
  </configuration>
</monitors>


```

Weirdly you can see here that 60Hz mode *is* set.

Here is EDID data according to "xrandr --prop" which is always the same regardless of whether the 60Hz option is available or not

```

00ffffffffffff001e6de476bd4e0600
091d0104b55022789eca95a6554ea126
0f50542108007140818081c0a9c0b300
d1c081000101e77c70a0d0a029503020
3a00204f3100001a9d6770a0d0a02250
30203a00204f3100001a000000fd0038
3d1e5a20000a202020202020000000fc
004c4720554c545241574944450a0121
020316712309060749100403011f1359
5a12830100009f3d70a0d0a015503020
3a00204f3100001a7e4800e0a0381f40
40403a00204f31000018011d007251d0
1e206e285500204f3100001e8c0ad08a
20e02d10103e9600204f310000180000
00000000000000000000000000000000
000000000000000000000000000000aa

```

I'm not sure how to decode this because I don't have root access on the machine I am using so I cannot install edid-parse.

It would be great if anyone could answer these questions:


[LIST=1]
[*]Is it possible to downgrade all the packages that were updated during a system update?
[*]If not - which package of those listed above could possibly have caused this issue?
[*]Why would xrandr sometimes show 60Hz as an available refresh rate and other times not?
[/LIST]

If anyone can provide any insight I'd be extremely grateful. If there is additional information you would like me to provide please let me know.

---

### Post by Autodave on 2020-06-01
How about giving us the make/model of your laptop.  Have you installed any video card drivers?  If so, what one{s} and where did you get them from?

---

### Post by aspz on 2020-06-01
My laptop is the Dell XPS 13 9380. I don't think there are any video card drivers installed but I am not sure how to discover this given that I don't have root access so I can't run any sudo commands.

---

### Post by aspz on 2020-06-02
Update: I have since ordered a USB-C to USB-C cable which supports HDMI video and using this cable works fine at 60Hz. Previously I was using a USB-C to Displayport cable. I am not sure whether the cable is the real issue here as the displayport cable was working fine for months before the update. It's possible there has been a regression in one of the packages that affects displayport.

---

