---
title: "SD-HC card not working"
date: 2013-01-04
forum: Hardware
---

### Post by nutricola on 2013-01-04
Hi all
I am using  Ubuntu 12.10 installed on a Laptop Asus S56C.
I tried to read an SDD card (8GB) through the Card reader of the laptop and nothing, I e tried another card and the result was the same. Also using an USB-card reader.

Both cards and the card reader are perfectly working in other computer and laptop.
doing a dmesg I got this (I post only the new part which appears after I insert the card):
```
[ 4137.716016] usb 3-2: new full-speed USB device number 11 using xhci_hcd
[ 4137.716085] usb 3-2: Device not responding to set address.
[ 4137.919811] usb 3-2: Device not responding to set address.
[ 4138.123510] usb 3-2: device not accepting address 11, error -71
[ 4138.179496] hub 3-0:1.0: unable to enumerate USB device on port 2

```

doing ls /dev/sd*  I got this (independently whether I have the card inserted or not) 
```
[ 4137.716016] usb 3-2: new full-speed USB device number 11 using xhci_hcd
[ 4137.716085] usb 3-2: Device not responding to set address.
[ 4137.919811] usb 3-2: Device not responding to set address.
[ 4138.123510] usb 3-2: device not accepting address 11, error -71
[ 4138.179496] hub 3-0:1.0: unable to enumerate USB device on port 2

```

lsusb:
```
Bus 003 Device 002: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```

lspci:
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Device 0153 (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 7 Series/C210 Series Chipset Family Thermal Management Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de3 (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)

```

Any idea?

---

### Post by Vakman on 2013-01-04
Try this if it is a Realtek card reader: [https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/971876](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/971876)

```
wget http://planet76.com/drivers/realtek/rts-bpp-dkms_1.1_all.deb
sudo apt-get install dkms
sudo dpkg -i rts-bpp-dkms_1.1_all.deb
echo 'DRIVERS=="rts_bpp", ENV{ID_DRIVE_FLASH_SD}="1"' | sudo tee -a /lib/udev/rules.d/81-udisks-realtek.rules
```

The above is from the link.

---

### Post by akshay.bhardwaj on 2013-01-04
You can check for solution here - [http://www.geekdevs.com/2010/04/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/](http://www.geekdevs.com/2010/04/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/)

---

### Post by nutricola on 2013-01-04
Thanks to both

the solution using
sudo sh -c 'echo -n "0000:00:xx.x" > unbind'
did not work. Actually I tried before posting my  post here.

The installation of the realtek drivers instead solved the problem.:guitar:
I am not able to change it to SOLVED.

---

### Post by honualive on 2013-01-04
> **nutricola said:**
> Thanks to both

the solution using
sudo sh -c 'echo -n "0000:00:xx.x" > unbind'
did not work. Actually I tried before posting my  post here.

The installation of the realtek drivers instead solved the problem.:guitar:
I am not able to change it to SOLVED.
How did you install the driver? I'm kinda clueless here... :noob:

---

### Post by nutricola on 2013-01-10
Just follow the steps described by THisislaw

---

