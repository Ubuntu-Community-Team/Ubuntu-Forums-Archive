---
title: "Do USB mice and keyboard get power saved ?"
date: 2021-10-24
forum: Hardware
---

### Post by adsb on 2021-10-24
Trying Ubuntu 21.10 server on a Raspberry Pi 3B+, installing xubuntu-desktop on the server.
I've tried 64 and 32 bit images - both behave the same.  Using a USB keyboard and a USB
mouse (Microsoft Optical).  They both work fine when running Raspbian on the Pi.

On Ubuntu, after some minutes of inactivity, the mouse buttons cease to work..The pointer works
fine, just the buttons pack up. If I unplug the mouse and then plug it in again, the buttons
still don't work.
I can do a "systemctl restart lightdm" to get the mouse working, but again after inactivity the
buttons pack up.

Xorg.0.log is interesting.  Something removes the mouse and keyboard devices - no idea what,
it isn't done by the user:  Makes me wonder if it's some power saving mechanism ?

[    40.688] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event0)
[    40.688] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "libinput pointer catchall"
[    40.688] (II) Using input driver 'libinput' for 'Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)'
[    40.688] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
[    40.688] (**) Option "Device" "/dev/input/event0"
[    40.689] (**) Option "_source" "server/udev"
[    40.765] (II) event0  - Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): is tagged by udev as: Mouse
[    40.766] (II) event0  - Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): device is a pointer
[    40.769] (II) event0  - Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): device removed
[    40.809] (**) Option "config_info" "udev:/sys/devices/platform/soc/3f980000.usb/usb1/1-1/1-1.2/1-1.2:1.0/0003:045E:0040.0001/input/input0/event0"
[    40.809] (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE, id 7)
[    40.810] (**) Option "AccelerationScheme" "none"
[    40.810] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) selected scheme none/0
[    40.810] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration factor: 2.000
[    40.810] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration threshold: 4
[    40.875] (II) event0  - Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): is tagged by udev as: Mouse
[    40.891] (II) event0  - Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): device is a pointer
[    40.896] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[    40.897] (II) No input driver specified, ignoring this device.
[    40.897] (II) This device may have been added with another device file.
[  1214.535] (II) event1  - Dell Dell Smart Card Reader Keyboard: device removed
[  1214.554] (II) event0  - Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): device removed

---

### Post by adsb on 2021-10-26
Ah, it's something in xubuntu-desktop.
I removed xubuntu-desktop, installed lubuntu-desktop and all is well.  Been running for over 12 hours and no "device removed" entries in Xorg.0.log

---

### Post by mastablasta on 2021-10-28
also, just for information, some mice and keyboards have a chip that saves certain settings. for example DPI, illumination, as well as some other settings.

---

