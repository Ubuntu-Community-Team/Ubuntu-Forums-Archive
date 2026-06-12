---
title: "Touchpad doesn't work after upgrading to Ubuntu 24.04.1 | System76 Pangolin"
date: 2024-10-04
forum: Hardware
---

### Post by helotbc-0 on 2024-10-04
The onboard touch pad was working under Ubuntu 23.10. I performed a system update to Ubuntu 24.04.1 and the touch pad has stopped working. It works when the logon screen appears. When I enter my password and press enter, the touchpad stops working. Things I have tried:
[LIST]
[*]Boot to a USB drive with 24.04.1 and the symptom is the same.
[*]Edit /etc/default/grub withGRUB_CMDLINE_LINUX_DEFAULT="quiet splash modprobe.blacklist=psmouse i8042.noaux"... no change
[*]Run modprobe -r i2c_hid /and/ modprobe i2c_hid... no change
[/LIST]

Other information is:

lsusb
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 2808:9348 Focal-systems.Corp FT9201Fingerprint.&#794;
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0e8d:0608 MediaTek Inc. Wireless_Device
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0c45:6809 Microdia USB2.0 Camera
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


xinput list
> &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer:15                         id=6    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-relative-pointer:15                id=7    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer-gestures:15                id=8    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; xwayland-keyboard:15 


sudo lshw
>   *-input:5
       product: PNP0C50:0b 0911:5288 Touchpad
       physical id: 6
       logical name: input7
       logical name: /dev/input/event4
       logical name: /dev/input/mouse1
       capabilities: i2c


less /proc/bus/input/devices
> I: Bus=0018 Vendor=0911 Product=5288 Version=0100
N: Name="PNP0C50:0b 0911:5288 Touchpad"
P: Phys=i2c-PNP0C50:0b
S: Sysfs=/devices/platform/AMDI0010:03/i2c-0/i2c-PNP0C50:0b/0018:0911:5288.0001/input/input7
U: Uniq=
H: Handlers=mouse1 event4 
B: PROP=5
B: EV=1b
B: KEY=e520 30000 0 0 0 0
B: ABS=2e0800000000003
B: MSC=20


I have read articles which mention that this issue could have its root in the kernel. Any thoughts would be appreciated.

---

