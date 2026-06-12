---
title: "Canon ip 2700 Printer Problems"
date: 2014-04-13
forum: Hardware
---

### Post by joe99 on 2014-04-13
Hi 

I am a total noob and need some help with my printer. My printer have been installed and did print fine until I ran out of ink. I tried to connect another ip2700 printer because Ididnt want to change it the cardriges that time (Was in a hurry) and thought well the drivers should be the same and tried to print the document. But well it didnt print. So I changed eventualy back to the original ip2700 that i originaly used to install the drivers, just changed the cardriges and now this one got the same symptomes. I can see the job in the printer "job card" but it just says pending and no printing happens. Checked the drivers and it seems fine. Although when i try to do the add printer thing through settings it searches for the printer finds it but when it has to instal the gutenprint driver the bar never moves :(. Here is the debugging I did in Terminal: 

Apr 13 21:07:20 joe-System-Product-Name kernel: [ 4048.059739] usblp0: removed
Apr 13 21:07:20 joe-System-Product-Name udev-configure-printer: remove /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3
Apr 13 21:07:38 joe-System-Product-Name kernel: [ 4065.914314] usb 2-1.3: new high-speed USB device number 12 using ehci-pci
Apr 13 21:07:38 joe-System-Product-Name kernel: [ 4066.008657] usb 2-1.3: New USB device found, idVendor=04a9, idProduct=10d3
Apr 13 21:07:38 joe-System-Product-Name kernel: [ 4066.008662] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Apr 13 21:07:38 joe-System-Product-Name kernel: [ 4066.008666] usb 2-1.3: Product: iP2700 series
Apr 13 21:07:38 joe-System-Product-Name kernel: [ 4066.008669] usb 2-1.3: Manufacturer: Canon
Apr 13 21:07:38 joe-System-Product-Name kernel: [ 4066.008671] usb 2-1.3: SerialNumber: 461460
Apr 13 21:07:38 joe-System-Product-Name kernel: [ 4066.011254] usblp 2-1.3:1.0: usblp0: USB Bidirectional printer dev 12 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10D3
Apr 13 21:07:38 joe-System-Product-Name mtp-probe: checking bus 2, device 12: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3"
Apr 13 21:07:38 joe-System-Product-Name mtp-probe: bus: 2, device: 12 was not an MTP device
Apr 13 21:07:38 joe-System-Product-Name udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0
Apr 13 21:07:38 joe-System-Product-Name udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0
Apr 13 21:07:38 joe-System-Product-Name udev-configure-printer: Device already handled
^C
joe@joe-System-Product-Name:~$ lsusb
Bus 002 Device 007: ID 12d1:155a Huawei Technologies Co., Ltd. 
Bus 002 Device 006: ID 04d9:a030 Holtek Semiconductor, Inc. 
Bus 002 Device 012: ID 04a9:10d3 Canon, Inc. 
Bus 002 Device 004: ID 1532:0036 Razer USA, Ltd RZ01-0075, Gaming Mouse [Naga Hex]
Bus 002 Device 003: ID 045e:070f Microsoft Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
joe@joe-System-Product-Name:~$ lsusb
Bus 002 Device 007: ID 12d1:155a Huawei Technologies Co., Ltd. 
Bus 002 Device 006: ID 04d9:a030 Holtek Semiconductor, Inc. 
Bus 002 Device 012: ID 04a9:10d3 Canon, Inc. 
Bus 002 Device 004: ID 1532:0036 Razer USA, Ltd RZ01-0075, Gaming Mouse [Naga Hex]
Bus 002 Device 003: ID 045e:070f Microsoft Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
joe@joe-System-Product-Name:~$ ls -l /dev/usb/lp* /dev/bus/usb/*/*
crw-rw-r--  1 root root 189,   0 Apr 13 19:59 /dev/bus/usb/001/001
crw-rw-r--+ 1 root root 189,   1 Apr 13 19:59 /dev/bus/usb/001/002
crw-rw-r--  1 root root 189,   2 Apr 13 19:59 /dev/bus/usb/001/003
crw-rw-r--  1 root root 189, 128 Apr 13 19:59 /dev/bus/usb/002/001
crw-rw-r--+ 1 root root 189, 129 Apr 13 19:59 /dev/bus/usb/002/002
crw-rw-r--  1 root root 189, 130 Apr 13 19:59 /dev/bus/usb/002/003
crw-rw-r--  1 root root 189, 131 Apr 13 19:59 /dev/bus/usb/002/004
crw-rw-r--  1 root root 189, 133 Apr 13 19:59 /dev/bus/usb/002/006
crw-rw-r--  1 root root 189, 134 Apr 13 19:59 /dev/bus/usb/002/007
crw-rw-r--  1 root lp   189, 139 Apr 13 21:07 /dev/bus/usb/002/012
crw-rw----  1 root lp   180,   0 Apr 13 21:07 /dev/usb/lp0
joe@joe-System-Product-Name:~$ sudo usb_printerid /dev/usb/lp0 
[sudo] password for joe: 
GET_DEVICE_ID string:
MFG:Canon;CMD:BJL,BJRaster3,BSCCe,IVEC,IVECPLI;SOJ:TXT01;MDL:iP2700 series;CLS:PRINTER;DES:Canon iP2700 series;VER:1.030;STA:10;FSI:00;HRI:EU;MSI:AOFF,BOFF,DAT,E3;PDR:4;
joe@joe-System-Product-Name:~$ sudo usb_printerid /dev/usb/lp1 
Error: No such file or directory: can't open '/dev/usb/lp1'
joe@joe-System-Product-Name:~$ sudo usb_printerid /dev/usb/lp1 
Error: No such file or directory: can't open '/dev/usb/lp1'
joe@joe-System-Product-Name:~$ sudo usb_printerid /dev/usb/lp0
GET_DEVICE_ID string:
MFG:Canon;CMD:BJL,BJRaster3,BSCCe,IVEC,IVECPLI;SOJ:TXT01;MDL:iP2700 series;CLS:PRINTER;DES:Canon iP2700 series;VER:1.030;STA:10;FSI:00;HRI:EU;MSI:AOFF,BOFF,DAT,E3;PDR:4;
joe@joe-System-Product-Name:~$ lpinfo -v
network ipp14
network beh
network lpd
network https
network smb
network ipps
network ipp
network socket
serial serial:/dev/ttyS0?baud=115200
network http
direct usb://Canon/iP2700%20series?serial=461460
direct parallel:/dev/lp0

Thats it hope it helps...

---

### Post by aikishugyo on 2014-04-14
Hi,
Clearly the printer is recognized at the USB level, that is good.
So now further information regarding printing would come from the CUPS error log. It has a default size of only 1MiB, so not sufficient for serious debugging.
In the CUPS interface ([http://localhost:631](http://localhost:631)) go to the Admin tab, 
[LIST=1]
[*] change the configuration of the logging to debug,
[*] edit the configuration file to set the size limit to much more than 1MiB
  (parameter is MaxLogSize and units are bytes), 
[*] restart CUPS service (it should be restartable from the Admin panel, but from command line also: "/etc/init.d/cups restart"), 
[*] and then try to print something.
[/LIST]

The error log file will then have information about CUPS in it, whether there is some problem or not should at least be clear from perusing that file.

---

