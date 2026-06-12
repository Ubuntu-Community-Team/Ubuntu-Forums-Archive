---
title: "Acer Switch 3 - Touchpad not recongnised"
date: 2018-10-08
forum: Hardware
---

### Post by turblety on 2018-10-08
I have an Acer Switch 3 that I'm trying to run Ubuntu 18 on.

Almost everything is working fine, the touchscreen and pen works well.

I can not, however, get the touchpad to work at all.

If I run `xinput --list` I get the following:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Chicony ACER Tablet Keyboard                id=9    [slave  pointer  (2)]
&#9116;   &#8627; 04F3224A:00 04F3:24FE                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; 04F3224A:00 04F3:24FE Pen Pen (0)           id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Chicony ACER Tablet Keyboard                id=8    [slave  keyboard (3)]
    &#8627; 04F3224A:00 04F3:24FE Pen                   id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=13    [slave  keyboard (3)]
    &#8627; Chicony ACER Tablet Keyboard                id=14    [slave  keyboard (3)]


```

In the BIOS I have tried changing the mouse setting to Standard and Advanced. Neither work.

I believe from reading online the problem lies with something to do with i2c, hid or something.

I have tried adding i8042.reset and i8042.nopnp and i8042.nomux in different variations to my kernel arguments, but nothing has worked.

I have tried hitting Fn+F7 multiple times through my different attempts at getting this to work.

I've also tried using `sudo evtest` to see if I can get a response out of anything, with no joy.

Outputting dmesg with a pnp grep gives me only:

```

[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-36-generic i8042.nopnp root=/dev/mmcblk1p2
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-36-generic i8042.nopnp root=/dev/mmcblk1p2
[    0.407184] pnp: PnP ACPI init
[    0.408695] pnp 00:01: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.410405] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.411586] pnp: PnP ACPI: found 4 devices

```

Before putting i8042.nopnp in the boot arguments I was getting a line saying:

```
i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
(the boot option i8042.nopnp doesn't work)
```

```

dmesg | grep mouse
[    3.843963] mousedev: PS/2 mouse device common for all mice
[    8.045756] usbcore: registered new interface driver usbmouse

```

```
[    3.843963] mousedev: PS/2 mouse device common for all mice
[    8.045756] usbcore: registered new interface driver usbmouse

```

```
dmesg | grep hid
[    4.250096] hidraw: raw HID events driver (C) Jiri Kosina
[    4.807847] usbcore: registered new interface driver usbhid
[    4.807857] usbhid: USB HID core driver
[    4.868439] hid-generic 0003:06CB:81A7.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony ACER Tablet Keyboard] on usb-0000:00:15.0-4/input0
[    4.892602] hid-rmi 0003:06CB:81A7.0003: failed to write hid report (-38)
[    4.892604] hid-rmi 0003:06CB:81A7.0003: rmi_set_page: set page failed: -38.
[    4.892606] hid-rmi 0003:06CB:81A7.0003: failed to set page select to 0.
[    4.893278] hid-rmi 0003:06CB:81A7.0003: hiddev0,hidraw1: USB HID v1.11 Mouse [Chicony ACER Tablet Keyboard] on usb-0000:00:15.0-4/input2
[    4.928550] hid-generic 0003:06CB:81A7.0002: input,hiddev1,hidraw2: USB HID v1.11 Device [Chicony ACER Tablet Keyboard] on usb-0000:00:15.0-4/input1
[    8.424315] i2c_hid i2c-04F3224A:00: i2c-04F3224A:00 supply vdd not found, using dummy regulator
[    9.197128] hid-multitouch 0018:04F3:24FE.0004: input,hidraw3: I2C HID v1.00 Device [04F3224A:00 04F3:24FE] on i2c-04F3224A:00

```

Some more information
```
lspci
00:00.0 Host bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Host Bridge (rev 0b)
00:00.1 Signal processing controller: Intel Corporation Device 5a8c (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Integrated Graphics Controller (rev 0b)
00:03.0 Multimedia controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Imaging Unit (rev 0b)
00:0e.0 Audio device: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster (rev 0b)
00:0f.0 Communication controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Trusted Execution Engine (rev 0b)
00:12.0 SATA controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SATA AHCI Controller (rev 0b)
00:14.0 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port B #2 (rev fb)
00:15.0 USB controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series USB xHCI (rev 0b)
00:16.0 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #1 (rev 0b)
00:16.1 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #2 (rev 0b)
00:16.3 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #4 (rev 0b)
00:17.0 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #5 (rev 0b)
00:17.1 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #6 (rev 0b)
00:1b.0 SD Host controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SDXC/MMC Host Controller (rev 0b)
00:1c.0 SD Host controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series eMMC Controller (rev 0b)
00:1f.0 ISA bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Low Pin Count Interface (rev 0b)
00:1f.1 SMBus: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SMBus Controller (rev 0b)
01:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)

lsusb
Bus 002 Device 002: ID 0781:5588 SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 06cb:81a7 Synaptics, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Anyone have any ideas how I can debug this further and get the touchpad to work?

---

### Post by turblety on 2018-10-08
Okay great news, I've managed to get somewhere thanks to an article [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1437759") (even though it's nothing to do with my tablet)

The steps I did to fix this was:

1. Open the terminal

2. Type:
```
sudo vi /etc/modules
```

3. Use the keyboard to navigate down to the very bottom of that file, then enter insert mode (type 'i')

4. Add the line:
```
hid_generic
```

5. Save the file (type ':wq')

6. You should now be at bash again, and can now type:
```
sudo vi /etc/modprobe.d/blacklist.conf
```

7. At the very bottom of that file, add the line:
```
blacklist hid_rmi
```

8. Save the file

9. Now you need to run the command below:
```
sudo echo 3 06cb 81a7 3 | sudo tee /sys/module/hid_generic/drivers/hid\:hid-generic/new_id
```

I really don't know where the two 3's came from, but I know the '06cb 81a7' is the device id as described in `xinput`. Anyway, I tried several combinations of numbers until I found the following line in dmesg, by grep'ing anything with "hid".

```
dmesg | grep hid
[    4.797290] hidraw: raw HID events driver (C) Jiri Kosina
[    4.825429] usbcore: registered new interface driver usbhid
[    4.825429] usbhid: USB HID core driver
[    4.912470] hid-generic 0003:06CB:81A7.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony ACER Tablet Keyboard] on usb-0000:00:15.0-4/input0
[    4.972684] hid-generic 0003:06CB:81A7.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Chicony ACER Tablet Keyboard] on usb-0000:00:15.0-4/input1
[    8.558227] i2c_hid i2c-04F3224A:00: i2c-04F3224A:00 supply vdd not found, using dummy regulator
[    8.945774] hid-multitouch 0018:04F3:24FE.0004: input,hidraw2: I2C HID v1.00 Device [04F3224A:00 04F3:24FE] on i2c-04F3224A:00
[   68.237546] hid-generic 0003:06CB:81A7.0003: input,hiddev1,hidraw3: USB HID v1.11 Mouse [Chicony ACER Tablet Keyboard] on usb-0000:00:15.0-4/input2

```

Note the very last line has 0003:06CB:81A7:0003, which translated to 3 06cb 81a7 3.

So for now running the above has got my trackpad working.

There is now a few remaining issues:

1. Every time I restart my tablet I must type the following to enable the trackpad. Is there anyway to make this run automatically. On the same thread I mentioned above they said to try adding it to '/etc/rc.local'. But on my Ubuntu 18 instance, that file does not exist:
```
sudo echo 3 06cb 81a7 3 | sudo tee /sys/module/hid_generic/drivers/hid\:hid-generic/new_id
```

2. The hard click doesn't work. Sometimes it performs a right click (bring up the context menu), but for the most it doesn't do anything. Light tap (tap-to-click) seems to work fine. It will even let me double tap to drag. Any ideas how I can make the hard click work?

3. Scrolling with two fingers doesn't work. I'm afraid this is just the case with using the generic hid driver, but does anyone have any ideas how I can make this work?

Thanks for your time reading!

---

### Post by ceres-c on 2018-10-09
Hi,
I am using Arch linux ATM and I have fixed my problem with the touchpad following your steps. Also, I don't get anymore a kernel paninc on keyboard disconnection (which was happening before).
You have to write in /etc/modprobe.d/hid.conf (you can give this file the name you want)
```
blacklist hid_rmi
```
Then in /etc/modules-load.d/hid.conf
```
hid_multitouch
```
Finally you rebuild the initramfs with
```
mkinitcpio -P
```

I didn't need to tee the device ID to the driver as it was simply working after a reboot. On the other side the problems you faced are present on my install too, but I believe the mouse click could be mapped somehow as a raw HID input.
Thanks for your input :)

---

