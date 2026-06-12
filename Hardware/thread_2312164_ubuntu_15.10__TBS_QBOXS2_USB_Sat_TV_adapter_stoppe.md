---
title: "ubuntu 15.10  TBS QBOXS2 USB Sat TV adapter stopped working"
date: 2016-02-02
forum: Hardware
---

### Post by Richard_Templeman on 2016-02-02
[SIZE=3]The driver for my USB adapter (TBS5928) was installed on ubuntu 15.10 a few days ago (after a real struggle) and I eventually got TVHeadend to scan channels on the Astra28.2E satellite.  I haven't had time to try to stream the video yet.

Yesterday,  the adapter no longer works on Ubuntu.  The only significant change was to [/SIZE][SIZE=3][SIZE=3]change (using grub-customiser) the grub2 boot loader to use a theme to make it prettier.  [/SIZE][/SIZE][SIZE=3][SIZE=3][SIZE=3][SIZE=3][SIZE=3](I have dual boot with Windows 8.1)
[/SIZE][/SIZE] [/SIZE]
[/SIZE]The adapter works fine on Windows 8.1 with DVBViewer software on the same PC[/SIZE][SIZE=3] and I have been using it for over 2 years.

I am at a loss to explain this as lsusb shows the device but the output from dmesg no longer has the messages showing the adapter "successfully initialised and connected".  Also hardinfo does not report any USB devices!


I have rebuilt the drivers and rebooted as recommended by the manufacturer to no effect.

Has anyone had a similar experience and has any ideas about what to try next?[/SIZE]



[SIZE=3]Here is the output from lsusb:
[SIZE=2]richard@zoostorm:~$ lsusb
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
[COLOR=#ff0000]Bus 001 Device 005: ID 734c:5928 TBS Technologies China Q-Box II DVB-S2 HD[/COLOR]
Bus 001 Device 004: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 0461:0010 Primax Electronics, Ltd HP PR1101U / Primax PMX-KPR1101U Keyboard
Bus 003 Device 003: ID 0461:4d64 Primax Electronics, Ltd 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
richard@zoostorm:~$ [/SIZE]
[/SIZE]
[SIZE=3][FONT=arial]This is the output I got previously from dmesg which is no longer present:[/FONT][/SIZE]
[FONT=arial narrow][SIZE=2][FONT=arial][COLOR=#000000]richard@zoostorm:~$ dmesg | grep QB
              [   16.851268] dvb-usb: found a 'TBS QBOXS2 DVBS2 USB2.0'               in cold state, will try to load a firmware
              [   17.298787] tbsqboxs2: start downloading TBSQBOX               firmware
              [   17.416612] dvb-usb: found a 'TBS QBOXS2 DVBS2 USB2.0'               in warm state.
              [   17.416850] DVB: registering new adapter (TBS QBOXS2               DVBS2 USB2.0)
              [   17.688764] QBOXS2: CX24116 attached.
              [   17.689349] dvb-usb: TBS QBOXS2 DVBS2 USB2.0               successfully initialized and connected.
              richard@zoostorm:~$ 
[/COLOR][/FONT][/SIZE][/FONT]
[FONT=arial narrow][SIZE=2][FONT=arial][COLOR=#000000][SIZE=3]4 Feb  More Info
sudo usbview shows the Device [/SIZE][/COLOR][COLOR=#ff0000][SIZE=3]TBS5928[/SIZE][/COLOR][COLOR=#000000][SIZE=3] in red - driver not installed

/var/log/syslog shows:
Feb  3 15:15:50 zoostorm kernel: [ 1773.141599] usb 1-1.4: USB disconnect, device number 5
Feb  3 15:16:01 zoostorm kernel: [ 1783.486999] usb 1-1.4: new high-speed USB device number 6 using xhci_hcd
Feb   3 15:16:01 zoostorm kernel: [ 1783.575417] usb 1-1.4: config 1  interface 0 altsetting 0 bulk endpoint 0x81 has[/SIZE][/COLOR][COLOR=#ff0000][SIZE=3] invalid maxpacket 2[/SIZE][/COLOR][COLOR=#000000][SIZE=3]
Feb  3 15:16:01 zoostorm kernel: [ 1783.575805] usb 1-1.4: New USB device found, idVendor=734c, idProduct=5928
Feb  3 15:16:01 zoostorm kernel: [ 1783.575809] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Feb  3 15:16:01 zoostorm kernel: [ 1783.575812] usb 1-1.4: Product: TBS 5928
Feb  3 15:16:01 zoostorm kernel: [ 1783.575814] usb 1-1.4: Manufacturer: TBS-Tech
Feb  3 15:16:01 zoostorm mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/usb1/1-1/1-1.4"
Feb  3 15:16:01 zoostorm mtp-probe: bus: 1, device: 6 was[/SIZE][/COLOR][COLOR=#ff0000][SIZE=3] not an MTP device[/SIZE][/COLOR][COLOR=#000000][SIZE=3]
[/SIZE]
[/COLOR][/FONT][/SIZE]
[/FONT]

---

