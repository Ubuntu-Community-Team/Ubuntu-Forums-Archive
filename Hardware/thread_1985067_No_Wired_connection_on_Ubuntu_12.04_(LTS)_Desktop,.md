---
title: "No Wired connection on Ubuntu 12.04 (LTS) Desktop, maybe after update(?)"
date: 2012-05-22
forum: Hardware
---

### Post by shayonj on 2012-05-22
Hello,

I am running Ubuntu 12.04 (LTS) and for some reason I cannot connect to the internet since this morning. It was working fine untill last. I cannot think of any reason for this strange, may be an update i did yesterday evening ? What could have possibly gone wrong. And how can I fix it ?

I have googled and searched the forums, but could not find a solution.

---

### Post by rmil on 2012-05-22
If possible first try with other cable, different router/switcher port, etc and  than you try to check if the network driver is the problem using commands  like
```
dmesg
sudo route -n
ifconfig
lspci
```

Also you have to be more specific.
Do you have connection notification icon on your bar?
Can you access other network shares?
Do you have only problem with browser?

---

### Post by shayonj on 2012-05-22
Hello,

Yes I still see the notification icon. And it keeps connecting, but after few seconds it says Disconnected. Also I dont have any shares. I am just not able to connect to the internet. I tried running ```
dmesg
```, and it gave bunch of
```
eth0: no IPv6 routers present
```
Also here is the outputs
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:c3:0f:d0  
          inet6 addr: fe80::1e6f:65ff:fec3:fd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1776 errors:0 dropped:72 overruns:0 frame:0
          TX packets:4427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:148876 (148.8 KB)  TX bytes:1027669 (1.0 MB)
          Interrupt:53 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17990 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17990 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1611421 (1.6 MB)  TX bytes:1611421 (1.6 MB)

lspci 

00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:10.0 PIC: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 13)
00:10.1 PIC: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 13)
00:11.0 PIC: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 (rev 13)
00:11.1 PIC: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 (rev 13)
00:13.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:15.0 PIC: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers (rev 13)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 IDE interface: Marvell Technology Group Ltd. Device 91a3 (rev 11)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
03:00.0 VGA compatible controller: NVIDIA Corporation GF104 [GeForce GTX 460] (rev a1)
03:00.1 Audio device: NVIDIA Corporation GF104 High Definition Audio Controller (rev a1)
05:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
05:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
06:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
06:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
08:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
3f:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
3f:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
3f:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
3f:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
3f:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
3f:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
3f:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
3f:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
3f:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
3f:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
3f:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
3f:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
3f:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
3f:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
3f:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
3f:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
3f:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
3f:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
3f:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)


```

---

### Post by rmil on 2012-05-23
99% it is driver as you will see if you use google

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

Try if helps:
[http://askubuntu.com/questions/140540/rtl8111-8168b-not-worked-properly-in-12-04](http://askubuntu.com/questions/140540/rtl8111-8168b-not-worked-properly-in-12-04)

or wait until bug get corrected:(

---

### Post by darth62969 on 2012-05-23
i wonder if any other computers are connecting to the internet or the network... or if you have a different OS on the computer and if that OS connects to the internet. if both are false (as in the connection) it may be an issue with the router.

---

### Post by shayonj on 2012-05-23
okay !

---

### Post by shayonj on 2012-05-23
> **darth62969 said:**
> i wonder if any other computers are connecting to the internet or the network... or if you have a different OS on the computer and if that OS connects to the internet. if both are false (as in the connection) it may be an issue with the router.

I have openSUSE too. and connect internet on that one either. Also I dont use router. its direct ethernet connection.

---

### Post by shayonj on 2012-05-23
The driver did not fix it. What next should be done ? Do I need revert the update back or ?

---

### Post by rmil on 2012-05-25
> **shayonj said:**
> I have openSUSE too. and connect internet on that one either. Also I dont use router. its direct ethernet connection.

Unfortunately It proves the fact that driver is the problem. 
Try to google some newer/older driver.

---

