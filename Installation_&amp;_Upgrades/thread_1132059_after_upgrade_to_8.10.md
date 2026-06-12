---
title: "after upgrade to 8.10"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by tronnix75 on 2009-04-21
after i upgraded to 8.10, my network settings are not staying after reboot.  i am using a compaq business class pc.  there is a red warning icon on the network icon down in the toolbar, also since i have 2 network in this box i have the ethernet cord plugged into the onboard one and then one plugged into the pci slot in which ubuntu does not see it only the onboard one?  please help me to fix this.

---

### Post by kestrel1 on 2009-04-21
Post the output from```
ifconfig
```&```
lspci
```
Type both in a terminal.

---

### Post by tronnix75 on 2009-04-21
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:04:5a:7b:54:03  
          inet6 addr: fe80::204:5aff:fe7b:5403/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:3 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x1000 

eth1      Link encap:Ethernet  HWaddr 00:08:02:cc:d8:bf  
          inet addr:192.168.75.10  Bcast:192.168.75.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fecc:d8bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2364217 (2.3 MB)  TX bytes:125427 (125.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1136 (1.1 KB)  TX bytes:1136 (1.1 KB)

---

### Post by tronnix75 on 2009-04-21
lspci

root@jeff-desktop:~# lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
05:04.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)
root@jeff-desktop:~#

---

### Post by tronnix75 on 2009-04-21
it seems that network manager does not see eth0

---

### Post by tronnix75 on 2009-04-21
can anyone help

---

