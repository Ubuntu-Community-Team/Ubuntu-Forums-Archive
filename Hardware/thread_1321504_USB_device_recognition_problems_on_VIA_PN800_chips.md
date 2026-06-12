---
title: "USB device recognition problems on VIA PN800 chipset and Karmic"
date: 2009-11-10
forum: Hardware
---

### Post by Leslie_K. on 2009-11-10
Dear community, I'm in need of someone's help. My problem explained:
I have a Fujitsu-Siemens Amilo L7310GW notebook with the following specifications:
Chipset: VIA PN800 + VIA VT8235CE
CPU: Intel Celeron M360 1,4GHz
RAM: 2x256MB DDR 333MHz
I also have Ubuntu 9.10 Karmic installed, everything is up and running except one thing: the recognition of USB devices. I tried connecting my Corsair Flash Voyager pendrives, my Logitech mouse, my Samsung MP3 player, but none of them is recognised by the OS or mounted. I tried using the other USB ports (these laptops have 3 of them), but no luck.
The ports are not faulty, since Windows XP is detecting the devices (I just used a custom Live CD instead of ruining my existing Ubuntu installation).
Seeking for a cure I found a [thread]("http://ubuntuforums.org/showthread.php?t=705258") where Temüjin's workaround helped me to solve this problem partially, so if I plug one of my devices into the USB port and use the following commands in the Terminal, the devices are recognised and get mounted automatically:
```

sudo update-pciids; lspci | grep USB
sudo update-usbids; lsusb
lsmod | grep usb

```I still didn't manage to find out which of the commands is helping, but this is not a permanent solution, since I always have to do it when a new USB device is connected or I reboot the system. Here are the terminal outputs, maybe it is helping:
**sudo update-pciids; lspci | grep USB**
```

Downloaded daily snapshot dated     2009-10-22 03:15:02
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)

```**sudo update-usbids; lsusb**
```

sudo: update-usbids: command not found
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```**lsmod | grep usb**
```

usb_storage            52544  0 

```This is working only one time in a session, so if I want to plug another devices to one of the USB ports, I have to reboot my system first, then doing the trick mentioned above.
Any thoughts or suggestion? Please feel free to leave comment, everything is appreciated!

---

