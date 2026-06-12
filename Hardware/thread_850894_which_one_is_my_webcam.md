---
title: "which one is my webcam?"
date: 2008-07-06
forum: Hardware
---

### Post by vistasucksss on 2008-07-06
and can anybody tell me the best way to install it so ubuntu recognizes it? i will post the lspci here: and thanks in advance :)

chris@Cali-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
chris@Cali-PC:~$

---

### Post by vistasucksss on 2008-07-06
is my webcam not listed in this list? sorry i am new to all this still :X

---

### Post by Idzme on 2008-07-06
just plug it in, and give the command in teh terminal, then unplug it and open a new terminal window, and then give the command again. You probably mis one device in the list, that will be you're webcam. (that's how I did finf out)

GL
idzme

---

### Post by overdrank on 2008-07-06
> **vistasucksss said:**
> is my webcam not listed in this list? sorry i am new to all this still :X

the command ```
lsusb
``` may identify it better also.

---

### Post by vistasucksss on 2008-07-06
thanks for the replies guys. but this is a built-in webcam not an external input device... i did a little research and i believe it is called Cyberlink Youcam. i dont know if this is just a name of the software that runs it or if it is the actual name of the hardware. 

overdrank.. not sure if this will help but here are the results:
chris@Cali-PC:~$ lsusb
Bus 007 Device 002: ID 0408:030c Quanta Computer, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:0f0c Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
chris@Cali-PC:~$ 

thanks again :)

---

### Post by overdrank on 2008-07-06
> **vistasucksss said:**
> thanks for the replies guys. but this is a built-in webcam not an external input device... i did a little research and i believe it is called Cyberlink Youcam. i dont know if this is just a name of the software that runs it or if it is the actual name of the hardware. 

overdrank.. not sure if this will help but here are the results:
chris@Cali-PC:~$ lsusb
Bus 007 Device 002: ID 0408:030c Quanta Computer, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:0f0c Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
chris@Cali-PC:~$ 

thanks again :)

No that command will not help if it is a built in device. Sorry I can not help with web cams as I do not use them.

---

### Post by lswb on 2008-07-06
Do you know what the Quanta device is in the lsusb listing? They do make webcams. See if you have any likely suspects in /dev

  ls /dev/*vid*

anything like /dev/video or /dev/video1 listed?

Also you may find some clues in the /sys directory.

---

