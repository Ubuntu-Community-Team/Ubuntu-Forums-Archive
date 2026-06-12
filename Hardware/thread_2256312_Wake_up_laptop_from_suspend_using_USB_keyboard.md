---
title: "Wake up laptop from suspend using USB keyboard"
date: 2014-12-11
forum: Hardware
---

### Post by edison23 on 2014-12-11
Hi, I hope somebody will be able to help me out with this. I realize this question has been asked before, however I have been unable to solve the problem using the suggestion posted in here [http://ubuntuforums.org/showthread.php?t=1968487](http://ubuntuforums.org/showthread.php?t=1968487) (which seems to be the thread from which everyone is copypasting the solutions).

So, my exact situation is this: I have Asus N56V laptop, Dell KB212 external USB keyboard and Ubuntu 14.11.
My goal is to be able to wake the laptop up from sleep (S3 I believe, everything in RAM) by clicking a random key on the external keyboard.

Output of dmesg | grep -i "dell" is this:
```

# dmesg | grep -i "dell"
[    1.838774] usb 3-4: Product: Dell USB Entry Keyboard
[    1.838778] usb 3-4: Manufacturer: DELL
[    1.841846] input: DELL Dell USB Entry Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/0003:413C:2107.0003/input/input14
[    1.842008] hid-generic 0003:413C:2107.0003: input,hidraw2: USB HID v1.11 Keyboard [DELL Dell USB Entry Keyboard] on usb-0000:00:14.0-4/input0

```

Output of lsusb:
```
# lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 004: ID 1bcf:2883 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 413c:2107 Dell Computer Corp. 
Bus 003 Device 002: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Output of cat /proc/acpi/wakeup:
```
# cat /proc/acpi/wakeup 
Device    S-state      Status   Sysfs node
P0P1      S4    *disabled
PEG0      S4    *disabled  pci:0000:00:01.0
PEG1      S4    *disabled
PEG2      S4    *disabled
PEG3      S4    *disabled
XHC1      S3    *enabled   pci:0000:00:14.0
EHC1      S3    *enabled   pci:0000:00:1d.0
USB1      S3    *disabled
USB2      S3    *disabled
USB3      S3    *disabled
USB4      S3    *disabled
EHC2      S3    *enabled   pci:0000:00:1a.0
USB5      S3    *disabled
USB6      S3    *disabled
USB7      S3    *disabled
HDEF      S4    *disabled  pci:0000:00:1b.0
RP03      S4    *disabled
RP05      S4    *disabled
RP06      S4    *disabled
RP07      S4    *disabled
RP08      S4    *disabled
WLAN      S3    *disabled  pci:0000:03:00.0
RP04      S4    *disabled  pci:0000:00:1c.3
GLAN      S4    *disabled  pci:0000:04:00.0
LAN2      S4    *disabled
XHC      S4    *disabled
SLPB      S4    *enabled   platform:PNP0C0E:00

```

And the wakeup is enabled for the device:
```
# cat /sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/power/wakeup
enabled

```

I also have a udev rule (the state of the computer described above is after restart with the new udev rule):
```
# cat /etc/udev/rules.d/90-keyboardwakeup.rules
SUBSYSTEM=="usb", ATTRS{idVendor}=="413c", ATTRS{idProduct}=="2107" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"
```

Still the keyboard doesn't wake the computer up.

Could somebody point me to some solution, please?

Thanks a lot in advance.

---

