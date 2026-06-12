---
title: "webcam issue on ASUS F9SG"
date: 2008-06-27
forum: Hardware
---

### Post by marconicotera on 2008-06-27
Hi all, as per title i have an ASUS F9SG with UBUNTU 8.04 on. The problem is that using skype, the web cam starts, it switch the light on but when i make the test it stucks BLACK.
Of course also during conversations no video of me appears to nobody-
Any suggestions?

---

### Post by needhelpplease on 2008-06-27
You need to make sure you have the driver for it.

First step:

From a command line, use the lsusb command to find out which devices you have.  You can post the result here and we can go from there.

---

### Post by marconicotera on 2008-06-28
Thanks a lot for your reply here ' s what i have



Bus 007 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 08ff:1600 AuthenTec, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 007: ID 0bda:0116 Realtek Semiconductor Corp. 
Bus 004 Device 004: ID 174f:8a31  
Bus 004 Device 003: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

erwin@erwin-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 042e (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
erwin@erwin-laptop:~$

The webcam is a D-MAX (STK-2135) 
Where can i find the drivers?????

I also tried Ekiga, same thing the cam starts but blank screen!!!

---

### Post by marconicotera on 2008-06-29
Any idea?????

---

