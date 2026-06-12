---
title: "Touchscreen, Wacom tablet and touchpad work, but not mouse"
date: 2010-03-04
forum: Hardware
---

### Post by monstara on 2010-03-04
Hi,
I recently got an HP DV3 laptop.
I somehow got the ATI Radeon card and the touchscreen (Wacom ISDv4 E2) to work in Karmic.
While doing this I compiled a new kernel (2.6.33) as instructed [here]("http://neo-technical.wikispaces.com/radeon-kms"). I also use self-compiled LinuxWacom drivers for the touchscreen (and hotplugging now also works for an external Wacom Graphire 4).
Surprisingly everything worked, but my plain old Logitech optical mouse stopped. Attaching OTHER USB mice had the same result.
I suspect it is a kernel config setting or a missing module. 

In short, the mouse appears in dmesg, lsusb and lshal (attached) but not /proc/bus/input/devices. It gets mapped to /dev/usb/hiddev0 (works if I *cat* it), but does not appear as /dev/input/mouse* or anywhere in /dev/input. I cleared all input device sections in xorg.conf, since everything else seemed to function well either way (only the video card seems to really need that).
From dmesg:
```

generic-usb 0003:046D:C016.0003: hiddev96,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1.1/input0

```It seems from other people's logs that among hiddev and hidraw, *input* should appear too.
I also attach the options with which I built my kernel. Just now I saw that CONFIG_HID_LOGITECH=m. Could this be the problem?

---

### Post by monstara on 2010-05-05
bump...

---

