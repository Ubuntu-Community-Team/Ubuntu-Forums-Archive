---
title: "-eee, EeePc 901/3G from Singtel"
date: 2008-11-11
forum: Hardware
---

### Post by agatek on 2008-11-11
This is a bit hermetic message as it mainly concerns Singapore Singtel EeePC users but I was looking for such message to make the purchasing decision and I failed to find any so for the record and the webcrawlers sake...

Asus together with Singtel offers EeePC 901 with a 3G modem on board and windows XP as the only choice of OS. I could not find what is there inside (the modem was the main concern) but I bough it anyway and it happened that the modem is Huawei E620. There are 2 8GB SSD included (sda/sdb) and the rest of the staff similar to the regular models. More hardware info below.

I am completely fresh to ubuntu - I typically use redhat/fedora things but I installed ubuntu eee (8.04) on the pc as it was said to be tailored to better fit this system. This is the experience so far in short:
Modem: There is no problem whatsoever with making the modem working as it is correctly detected via usbstorage/serial and ttyUSBx devices are created. One can get so lazy (my case) to simply run wvdialconf and later only add the provider data to the config file and it already works. For Singtel I used the "stupid mode" as apparently Singtel does not generate any prompt. Other things that work out of box:
- video
- sound
- wireless
- ethernet
- other usual and minor staff.

Not checked yet:
- camera
- BT

There are some problems with the grub bitmap so the boot loader window is black but this is obviously minor. So all together looks like highly compatibile hardware (should be expected) including the modem.

lspci and lsusb results:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: RaLink Unknown device 0781
04:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
Bus 005 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 005 Device 002: ID 058f:6335 Alcor Micro Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Marcin

---

