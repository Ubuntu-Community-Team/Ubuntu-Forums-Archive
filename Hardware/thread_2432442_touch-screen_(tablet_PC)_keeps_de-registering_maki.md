---
title: "touch-screen (tablet PC) keeps de-registering making system unusable"
date: 2019-12-02
forum: Hardware
---

### Post by artelius on 2019-12-02
I have a tablet PC (Yoga Book C930) with Wacom support which **worked fine for a few months.** A few weeks ago it became incredibly slow and often the window manager seems to restart or the desktop manager restarts entirely. (Windows is also installed and no problems there.)

In [FONT=courier new]dmesg[/FONT] it seems that the USB HID device(s) are constantly being de-registered and re-registered. The problem is there is no *reason* given for being de-registered and it does not happen at predictable intervals. Occasionally it's fine for a minute but then starts doing it every few seconds.

This is happening with the stock Ubuntu 18.04 with all the latest updates. Unfortunately I am not sure exactly when it broke. However I know for sure that things worked in the past when I was e.g. using kernel 4.15.0-51 and a few later ones. Now I have gone back and tried that kernel (4.15.0-51), which now **doesn't work anymore** and several later ones through to 4.15.0-70, with no success.

Just in case there were any kernel of userland updates that would help, I did an upgrade from 18.04 to 20.04 (kernel 5.3.0) which did not fix the problem..

I get this kind of loop in dmesg:

```

    [  173.554396] usbcore: deregistering interface driver usbhid
    [  173.917015] hid-generic 0003:048D:8951.008D: hiddev0,hidraw0: USB HID v1.11 Device [ITE Tech. Inc. ITE T-CON] on usb-0000:00:14.0-7/input1
    [  173.929225] input: ITE Tech. Inc. ITE T-CON Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:048D:8951.008E/input/input795
    [  173.991177] input: ITE Tech. Inc. ITE T-CON Consumer Control as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:048D:8951.008E/input/input796
    [  173.991259] input: ITE Tech. Inc. ITE T-CON Wireless Radio Control as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:048D:8951.008E/input/input797
    [  173.991372] input: ITE Tech. Inc. ITE T-CON Touchpad as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:048D:8951.008E/input/input799
    [  173.991503] hid-multitouch 0003:048D:8951.008E: input,hiddev1,hidraw1: USB HID v1.11 Keyboard [ITE Tech. Inc. ITE T-CON] on usb-0000:00:14.0-7/input2
    [  174.019922] input: ITE Tech. Inc. ITE T-CON as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.3/0003:048D:8951.008F/input/input800
    [  174.020151] input: ITE Tech. Inc. ITE T-CON Pen as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.3/0003:048D:8951.008F/input/input803
    [  174.021248] hid-multitouch 0003:048D:8951.008F: input,hiddev2,hidraw2: USB HID v1.11 Mouse [ITE Tech. Inc. ITE T-CON] on usb-0000:00:14.0-7/input3
    [  174.022442] usbcore: registered new interface driver usbhid
    [  174.022443] usbhid: USB HID core driver
    [  174.044101] input: Wacom HID 5182 Pen as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-WCOM5182:00/0018:056A:5182.0002/input/input809
    [  174.044977] input: Wacom HID 5182 Finger as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-WCOM5182:00/0018:056A:5182.0002/input/input810
    [  174.045326] wacom 0018:056A:5182.0002: hidraw3: I2C HID v1.00 Mouse [WCOM5182:00 056A:5182] on i2c-WCOM5182:00
    [  174.900663] usbcore: deregistering interface driver usbhid
    [  175.315543] hid-generic 0003:048D:8951.0090: hiddev0,hidraw0: USB HID v1.11 Device [ITE Tech. Inc. ITE T-CON] on usb-0000:00:14.0-7/input1
    [  175.330506] input: ITE Tech. Inc. ITE T-CON Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:048D:8951.0091/input/input812
    [  175.391153] input: ITE Tech. Inc. ITE T-CON Consumer Control as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:048D:8951.0091/input/input813
    [  175.391338] input: ITE Tech. Inc. ITE T-CON Wireless Radio Control as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:048D:8951.0091/input/input814
    [  175.391482] input: ITE Tech. Inc. ITE T-CON Touchpad as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:048D:8951.0091/input/input816
    [  175.391604] hid-multitouch 0003:048D:8951.0091: input,hiddev1,hidraw1: USB HID v1.11 Keyboard [ITE Tech. Inc. ITE T-CON] on usb-0000:00:14.0-7/input2
    [  175.421713] input: ITE Tech. Inc. ITE T-CON as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.3/0003:048D:8951.0092/input/input817
    [  175.421999] input: ITE Tech. Inc. ITE T-CON Pen as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.3/0003:048D:8951.0092/input/input820
    [  175.423156] hid-multitouch 0003:048D:8951.0092: input,hiddev2,hidraw2: USB HID v1.11 Mouse [ITE Tech. Inc. ITE T-CON] on usb-0000:00:14.0-7/input3
    [  175.423290] usbcore: registered new interface driver usbhid
    [  175.423291] usbhid: USB HID core driver
    [  175.451410] input: Wacom HID 5182 Pen as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-WCOM5182:00/0018:056A:5182.0002/input/input826
    [  175.451770] input: Wacom HID 5182 Finger as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-WCOM5182:00/0018:056A:5182.0002/input/input827
    [  175.452257] wacom 0018:056A:5182.0002: hidraw3: I2C HID v1.00 Mouse [WCOM5182:00 056A:5182] on i2c-WCOM5182:00
    [  178.469147] usbcore: deregistering interface driver usbhid
    [  178.870459] hid-generic 0003:048D:8951.0093: hiddev0,hidraw0: USB HID v1.11 Device [ITE Tech. Inc. ITE T-CON] on usb-0000:00:14.0-7/input1
    [  178.885441] input: ITE Tech. Inc. ITE T-CON Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:048D:8951.0094/input/input829
    [  178.943631] input: ITE Tech. Inc. ITE T-CON Consumer Control as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:048D:8951.0094/input/input830
    [  178.943746] input: ITE Tech. Inc. ITE T-CON Wireless Radio Control as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:048D:8951.0094/input/input831
    [  178.943857] input: ITE Tech. Inc. ITE T-CON Touchpad as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.2/0003:048D:8951.0094/input/input833
    [  178.944073] hid-multitouch 0003:048D:8951.0094: input,hiddev1,hidraw1: USB HID v1.11 Keyboard [ITE Tech. Inc. ITE T-CON] on usb-0000:00:14.0-7/input2
    [  178.971708] input: ITE Tech. Inc. ITE T-CON as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.3/0003:048D:8951.0095/input/input834
    [  178.971921] input: ITE Tech. Inc. ITE T-CON Pen as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.3/0003:048D:8951.0095/input/input837
    [  178.974611] hid-multitouch 0003:048D:8951.0095: input,hiddev2,hidraw2: USB HID v1.11 Mouse [ITE Tech. Inc. ITE T-CON] on usb-0000:00:14.0-7/input3
    [  178.975352] usbcore: registered new interface driver usbhid
    [  178.975354] usbhid: USB HID core driver
    [  178.999887] input: Wacom HID 5182 Pen as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-WCOM5182:00/0018:056A:5182.0002/input/input843
    [  179.000273] input: Wacom HID 5182 Finger as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-WCOM5182:00/0018:056A:5182.0002/input/input844
    [  179.000633] wacom 0018:056A:5182.0002: hidraw3: I2C HID v1.00 Mouse [WCOM5182:00 056A:5182] on i2c-WCOM5182:00
    [  184.761394] usbcore: deregistering interface driver usbhid
    [  185.165085] hid-generic 0003:048D:8951.0096: hiddev0,hidraw0: USB HID v1.11 Device [ITE Tech. Inc. ITE T-CON] on usb-0000:00:14.0-7/input1
```

etc.

I'd like to highlight these lines:

[HTML][HTML]```
    [  173.554396] usbcore: deregistering interface driver usbhid
    [  174.022442] usbcore: registered new interface driver usbhid
    [  174.022443] usbhid: USB HID core driver
    [  174.900663] usbcore: deregistering interface driver usbhid
    [  175.423290] usbcore: registered new interface driver usbhid
    [  175.423291] usbhid: USB HID core driver
    [  178.469147] usbcore: deregistering interface driver usbhid
    [  178.975352] usbcore: registered new interface driver usbhid
    [  178.975354] usbhid: USB HID core driver
    [  184.761394] usbcore: deregistering interface driver usbhid
```

If I blacklist `usbhid` (while the system is running) the problem is gone and when I un-blacklist it (while the system is running) it comes back.

Note that the "deregistering" entries come out of the blue a few seconds  after the previous log entry. They do not seem to be "triggered" by  anything. I am wondering whether there is somewhere I can get more detailed output about USB goings-on? (I have already tried log level 7.) I have experience writing drivers so I can get my hands pretty dirty but I'm not sure where to start.

Any other ideas? Thanks!

---

### Post by artelius on 2019-12-04
I have now installed Arch and do not have this problem. This indicates it is not the problem with the device itself; most likely it is due to some recent userland upgrade (X, udev, or something.) I've tried lightdm instead of gdm3 and it's no better.

---

