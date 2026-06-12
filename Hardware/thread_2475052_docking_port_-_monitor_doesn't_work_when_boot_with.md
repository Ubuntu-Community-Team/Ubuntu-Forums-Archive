---
title: "docking port - monitor doesn't work when boot with docking port plugged in"
date: 2022-05-15
forum: Hardware
---

### Post by gleedadswell on 2022-05-15
OK, this is a very minor issue, and there are many workarounds I could do.  But I'd like to see if I can resolve it, partly to learn more about how devices are recognized by the OS.

I have a  HP Omen 16-B0008CA laptop
16X i7-11800H @ 2.3 GHz core
Geforce RTX 3060 Max-Q

I'm running a new fairly new install of Ubuntu 22.04

```
geoff@geoff-HP-kubo-laptop:~$ uname-r
5.15.0-30-generic
``` 

I also have an Anker PowerExpand 8-in-1, product number A8383, usb-c docking port.  If I boot the computer without the docking port connected, then connect it then everything seems to work (usb-A ports work, usb-C ports work, hdmi port works, haven't tried the ethernet port or the SD card reader).  But if I boot the computer with the docking port already connected then the usb-A and usb-C ports work, but the hdmi port doesn't.  I've done a little bit of poking around and here's what I've found.  At the risk of providing a flood of information that is hard to read, here it is:

Running xrandr with the second monitor attached via the hdmi port in the docking port and working (i.e. when dock plugged in after boot) gives:

```
geoff@geoff-HP-kubo-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 16384 x 16384
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 355mm x 199mm
.....
<a big list of display modes, which I will spare you from...>
.....
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-2 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 480mm x 270mm
....
<list of modes>
....
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 disconnected (normal left inverted right x axis y axis)
DVI-I-5-4 disconnected (normal left inverted right x axis y axis)
DVI-I-4-3 disconnected (normal left inverted right x axis y axis)
DVI-I-3-2 disconnected (normal left inverted right x axis y axis)
DVI-I-2-1 disconnected (normal left inverted right x axis y axis)
HDMI-1-0 disconnected (normal left inverted right x axis y axis)
DP-1-0 disconnected (normal left inverted right x axis y axis)
DP-1-1 disconnected (normal left inverted right x axis y axis)


```

So, the monitor connected via the hdmi in the docking port is DP-2.  If I disconnect it, or if I boot with the docking port connected so that the monitor doesn't work then the part of that about DP-2 just changes to

```
DP-2 disconnected (normal left inverted right x axis y axis)
```

If I've connected the docking port after boot (so everything works) then udev sees when I plug in or unplug the monitor to the docking port.  Plugging it in I get:

```
geoff@geoff-HP-kubo-laptop:~$ sudo udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent


KERNEL[700.723867] add      /devices/pci0000:00/0000:00:02.0/rc/rc0 (rc)
KERNEL[700.724111] add      /devices/pci0000:00/0000:00:02.0/rc/rc0/input37 (input)
KERNEL[700.724205] add      /devices/pci0000:00/0000:00:02.0/rc/rc0/input37/event26 (input)
KERNEL[700.724423] add      /devices/pci0000:00/0000:00:02.0/cec0 (cec)
UDEV  [700.725758] add      /devices/pci0000:00/0000:00:02.0/rc/rc0 (rc)
UDEV  [700.725834] add      /devices/pci0000:00/0000:00:02.0/cec0 (cec)
KERNEL[700.726215] change   /devices/pci0000:00/0000:00:02.0/drm/card4 (drm)
UDEV  [700.726534] add      /devices/pci0000:00/0000:00:02.0/rc/rc0/input37 (input)
UDEV  [700.729745] change   /devices/pci0000:00/0000:00:02.0/drm/card4 (drm)
UDEV  [700.765302] add      /devices/pci0000:00/0000:00:02.0/rc/rc0/input37/event26 (input)
```

and unplugging it I see

```
KERNEL[724.334106] change   /devices/pci0000:00/0000:00:02.0/drm/card4 (drm)UDEV  [724.338974] change   /devices/pci0000:00/0000:00:02.0/drm/card4 (drm)
KERNEL[728.139746] remove   /devices/pci0000:00/0000:00:02.0/rc/rc0/input37/event26 (input)
UDEV  [728.147935] remove   /devices/pci0000:00/0000:00:02.0/rc/rc0/input37/event26 (input)
KERNEL[728.187459] remove   /devices/pci0000:00/0000:00:02.0/rc/rc0/input37 (input)
KERNEL[728.187506] remove   /devices/pci0000:00/0000:00:02.0/cec0 (cec)
UDEV  [728.187970] remove   /devices/pci0000:00/0000:00:02.0/rc/rc0/input37 (input)
UDEV  [728.188670] remove   /devices/pci0000:00/0000:00:02.0/cec0 (cec)
```

If I boot with the docking port connected then plugging in and unplugging the monitor to the hdmi on the docking port produces no events that udevadm sees.

If I boot without the docking port connected then when I plug in the docking port, with the monitor already plugged into the docking port's hdmi port, it generates the following in the logs:

```
geoff@geoff-HP-kubo-laptop:~$ sudo dmesg | grep "DP-2"
[   62.499248] rc rc0: DP-2 as /devices/pci0000:00/0000:00:02.0/rc/rc0
[   62.499271] input: DP-2 as /devices/pci0000:00/0000:00:02.0/rc/rc0/input30
```

If I boot with the docking port connected then no messages like this appear in the logs.  I've searched for error messages in the logs to do with attempts to set a device "rc/rc0", but haven't found anything.

I know how to probe for connections/disconnections of devices in the ways I've done above.  But I don't know how to (say) force the system to look for the hdmi port on the docking port.  Ideas of what to try next?

---

