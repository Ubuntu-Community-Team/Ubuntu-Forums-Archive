---
title: "Toshiba Satellite L500D wireless nic"
date: 2010-02-12
forum: Hardware
---

### Post by slo82 on 2010-02-12
Hello all. Im sure this has been asked 100 times even more but i cant get the wireless to work. im actually jumping ship from Fedora Core and really hate Windows 7 so id like to have Ubuntu setup wireless for starters, i think most other drivers are working straight out of the box for now.

anyway im as rusty as it gets with all this, i did some searches, but everything was really really old and not my exact machine so id always hit a wall and get stuck as id try follow the parths of others. 

i have a fresh copy of Ubuntu 9.10 installed (dual boooting for the miss with Windows 7 successfully) so now to keep this machine portable can someone please help me with the Wireless, i know its a easy task for someone in the know, i have set up wireless on an older laptop of mine quite a while ago in Fedora so although i cant remember much at all i still am familiar with terminal etc.

any help will be greatly appreciated.

---

### Post by mikewhatever on 2010-02-12
Take a look at System->Admin->Hardware Drivers. If there is a driver for your wireless, try installing (need ethernet connected). If that doesn't work, post the output of <lspci> to determine the chipset.

---

### Post by slo82 on 2010-02-12
that HARDWARE DRIVERS APP actually installed a graphics driver so u helped with something else lol, thanx for that.... 

anyway here is what i have thanx

:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9713
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by mikewhatever on 2010-02-12
It looks like you have a Realtek wireless card.

```
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
```

Here is a rather recent and successful solution:

[http://forums.linuxmint.com/viewtopic.php?f=53&t=38981](http://forums.linuxmint.com/viewtopic.php?f=53&t=38981)

...and another

[https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

---

### Post by slo82 on 2010-02-12
i think i got through to step 10 then hit a wall? im sure its obvious but im trully just copieing and pasting this stuff with almost no idea what im doing.

slo82@slo82-laptop:~/Desktop$ cd rtl8192se_linux_2.6.0010.1012.2009
slo82@slo82-laptop:~/Desktop/rtl8192se_linux_2.6.0010.1012.2009$ sudo su -
root@slo82-laptop:~# make
make: *** No targets specified and no makefile found.  Stop.
root@slo82-laptop:~# make install
make: *** No rule to make target `install'.  Stop.
root@slo82-laptop:~# 


when i got to the "make install" i lost it all....

[http://forum.novatech.co.uk/showthread.php?p=197789](http://forum.novatech.co.uk/showthread.php?p=197789)

it wasw step 10 on the following link

---

### Post by slo82 on 2010-02-12
got past step 10, did everything it said and looked like everything happened like it should.   BUT still no wireless...   can someone help, cos the tuturial said that if i reboot it will work,   i rebooted and nothing

---

### Post by mikewhatever on 2010-02-12
Do make sure the wireless is turned on, in case there is a button or switch. If that's not the problem, post the outputs of:

lsmod | grep r8192se_pci

sudo lshw -C network

---

### Post by slo82 on 2010-02-12
thanx a lot for all this help mate. greatly appreciated 

*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:a000(size=256) memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:ea:80:f8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.7 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:b000(size=256) memory:f0410000-f0410fff(prefetchable) memory:f0400000-f040ffff(prefetchable) memory:f0420000-f043ffff(prefetchable)

---

### Post by mikewhatever on 2010-02-12
So the lsmod command gave no output? If so run <sudo modprobe r8192se_pci>. Hopefully, that will bring the wireless to life, and if it does, just add the r8192se_pci module to /etc/modules to make sure it loads on startup.

---

### Post by slo82 on 2010-02-12
i appoligise for being so hopeless here, but that didnt work...

:~$ sudo modprobe r8192se_pci
[sudo] password for slo82: 
FATAL: Module r8192se_pci not found.

what does that mean?

---

### Post by mikewhatever on 2010-02-12
That means it can't find the specified module, not quite sure why.

---

### Post by slo82 on 2010-02-12
thanx for your time mate... 

maybe ill try a fresh install and make sure everything is updated then ill try again...

wish me luck

---

### Post by mikewhatever on 2010-02-12
Yea, good luck. 
What's odd is, I just looked through dmesg on Dell mini 10, troubleshooting sound configurations, and apparently, the ethernet card is Realtek. The modules, r8169 just loads, no problem, never had to install it manually.

---

