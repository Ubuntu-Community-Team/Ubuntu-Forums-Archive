---
title: "Elantech touchpad freezes"
date: 2013-07-08
forum: Hardware
---

### Post by snowak on 2013-07-08
I have Asus Zenbook UX32VD with Elantech touchpad. Everything worked perfectly until yesterday. Suddenly touchpad started freezing for few seconds.

Here's what I found in dmesg:

```
    [ 1880.241468] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
    [ 1880.319649] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
    [ 1880.381258] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
    [ 1920.454796] psmouse serio4: elantech: retrying ps2 command 0x07 (2).
    [ 1920.956651] psmouse serio4: elantech: retrying ps2 command 0x07 (1).
    [ 1921.657271] psmouse serio4: elantech: retrying ps2 command 0x07 (0).
    [ 1922.160484] psmouse serio4: elantech: ps2 command 0x07 failed.
    [ 1922.160496] psmouse serio4: elantech: failed to write register 0x07 with value 0x01.
    [ 1922.160501] psmouse serio4: elantech: failed to initialise registers.
    [ 1922.160505] psmouse serio4: elantech: failed to put touchpad back into absolute mode.
    [ 1922.372373] psmouse serio4: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
    [ 1922.559678] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f02)
    [ 1922.572142] psmouse serio4: elantech: Synaptics capabilities query result 0x00, 0x15, 0x0e.
    [ 1922.634331] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input19

```

So I've checked aptitude logs to check what packages were updated that day.
```
    [REMOVE, NOT USED] linux-headers-3.5.0-34:amd64
    [REMOVE, NOT USED] linux-headers-3.5.0-34-generic:amd64
    [INSTALL, DEPENDENCIES] linux-headers-3.5.0-36:amd64
    [INSTALL, DEPENDENCIES] linux-headers-3.5.0-36-generic:amd64
    [INSTALL, DEPENDENCIES] linux-image-3.5.0-36-generic:amd64
    [INSTALL, DEPENDENCIES] linux-image-extra-3.5.0-36-generic:amd64
    [UPGRADE] firefox:amd64 22.0+build2-0ubuntu0.12.10.1 -> 22.0+build2-0ubuntu0.12.10.2
    [UPGRADE] firefox-globalmenu:amd64 22.0+build2-0ubuntu0.12.10.1 -> 22.0+build2-0ubuntu0.12.10.2
    [UPGRADE] firefox-locale-en:amd64 22.0+build2-0ubuntu0.12.10.1 -> 22.0+build2-0ubuntu0.12.10.2
    [UPGRADE] google-chrome-stable:amd64 28.0.1500.70-r209565 -> 28.0.1500.71-r209842
    [UPGRADE] libdrm-dev:amd64 2.4.43-0ubuntu0.1 -> 2.4.43-0ubuntu0.2
    [UPGRADE] libdrm-intel1:amd64 2.4.43-0ubuntu0.1 -> 2.4.43-0ubuntu0.2
    [UPGRADE] libdrm-intel1:i386 2.4.43-0ubuntu0.1 -> 2.4.43-0ubuntu0.2
    [UPGRADE] libdrm-nouveau1a:amd64 2.4.43-0ubuntu0.1 -> 2.4.43-0ubuntu0.2
    [UPGRADE] libdrm-nouveau2:amd64 2.4.43-0ubuntu0.1 -> 2.4.43-0ubuntu0.2
    [UPGRADE] libdrm-nouveau2:i386 2.4.43-0ubuntu0.1 -> 2.4.43-0ubuntu0.2
    [UPGRADE] libdrm-radeon1:amd64 2.4.43-0ubuntu0.1 -> 2.4.43-0ubuntu0.2
    [UPGRADE] libdrm-radeon1:i386 2.4.43-0ubuntu0.1 -> 2.4.43-0ubuntu0.2
    [UPGRADE] libdrm2:amd64 2.4.43-0ubuntu0.1 -> 2.4.43-0ubuntu0.2
    [UPGRADE] libdrm2:i386 2.4.43-0ubuntu0.1 -> 2.4.43-0ubuntu0.2
    [UPGRADE] libgl1-mesa-dev:amd64 9.0.3-0ubuntu0.2 -> 9.0.3-0ubuntu0.4
    [UPGRADE] libgl1-mesa-dri:amd64 9.0.3-0ubuntu0.2 -> 9.0.3-0ubuntu0.4
    [UPGRADE] libgl1-mesa-dri:i386 9.0.3-0ubuntu0.2 -> 9.0.3-0ubuntu0.4
    [UPGRADE] libgl1-mesa-glx:amd64 9.0.3-0ubuntu0.2 -> 9.0.3-0ubuntu0.4
    [UPGRADE] libgl1-mesa-glx:i386 9.0.3-0ubuntu0.2 -> 9.0.3-0ubuntu0.4
    [UPGRADE] libglapi-mesa:amd64 9.0.3-0ubuntu0.2 -> 9.0.3-0ubuntu0.4
    [UPGRADE] libglapi-mesa:i386 9.0.3-0ubuntu0.2 -> 9.0.3-0ubuntu0.4
    [UPGRADE] libkms1:amd64 2.4.43-0ubuntu0.1 -> 2.4.43-0ubuntu0.2
    [UPGRADE] libssl1.0.0:amd64 1.0.1c-3ubuntu2.4 -> 1.0.1c-3ubuntu2.5
    [UPGRADE] libssl1.0.0:i386 1.0.1c-3ubuntu2.4 -> 1.0.1c-3ubuntu2.5
    [UPGRADE] libxatracker1:amd64 9.0.3-0ubuntu0.2 -> 9.0.3-0ubuntu0.4
    [UPGRADE] linux-generic:amd64 3.5.0.34.50 -> 3.5.0.36.52
    [UPGRADE] linux-headers-generic:amd64 3.5.0.34.50 -> 3.5.0.36.52
    [UPGRADE] linux-image-generic:amd64 3.5.0.34.50 -> 3.5.0.36.52
    [UPGRADE] linux-libc-dev:amd64 3.5.0-34.55 -> 3.5.0-36.57
    [UPGRADE] mesa-common-dev:amd64 9.0.3-0ubuntu0.2 -> 9.0.3-0ubuntu0.4
    [UPGRADE] openssl:amd64 1.0.1c-3ubuntu2.4 -> 1.0.1c-3ubuntu2.5
    [UPGRADE] xserver-xorg-video-intel:amd64 2:2.20.9-0ubuntu2.1 -> 2:2.20.9-0ubuntu2.2

```

I've tried using older kernel and even installing newer one, but with no luck. Does anybody have an idea how to fix this issue? Everything works perfectly fine on Windows.

---

