---
title: "Ethernet LAN is not working , help ..."
date: 2009-04-09
forum: Hardware
---

### Post by Dragon6 on 2009-04-09
Hi 
I Have Ubuntu 8.10 installed on my laptop Dell vostro 1510 which has Realtek RTL-8100C Ethernet that is not working at all
I need to connect to the internet through this interface
can anyone help please ?  Thanks in advance ...

---

### Post by askreet on 2009-04-09
Please open a terminal and paste the output of:

$ lspci

$ lsmod

$ ifconfig -a

You might want to use a USB thumb drive to copy the output to and then get it to the forum from a working PC.

If ifconfig -a shows eth0, then your network device is detected but failing to obtain an IP address.  Are you using DHCP in your network?

If eth0 is not displayed, then a proper driver for your network card could not be found, the output of `dmesg` might reveal something.  You could paste that here as well.

---

### Post by Dragon6 on 2009-04-09
Yes I'm using DHCP 
user-laptop:~$ lcpci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

user-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:e1:1b:37:c4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:133638 errors:0 dropped:0 overruns:0 frame:1012017
          TX packets:136121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:172606068 (172.6 MB)  TX bytes:14263962 (14.2 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29485 (29.4 KB)  TX bytes:29485 (29.4 KB)

pan0      Link encap:Ethernet  HWaddr d6:d8:1d:ee:55:f7  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Thank you ...

---

