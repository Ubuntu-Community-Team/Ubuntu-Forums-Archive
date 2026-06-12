---
title: "Cant get new Intel network adapter to work"
date: 2008-06-26
forum: Hardware
---

### Post by SteveNorman on 2008-06-26
I tried today to install a replacement for my ancient 10/100 network interface card. My new one is this:

	NIC INTEL|PWLA8391GTBLK GIGABIT 1PC  also known as :
        intel PRO/1000 GT Desktop Adapter

When I turned the computer on after install into a pci slot and connecting to my cable (comcast high sped),  I got to an intel boot agent screen before it went to grub. It said it was looking for Client Mac adde or somthing like that. this was working on screen:

DHCO\P............./ 

where (/) was rotating to indicate working.

 It said something very quickly that I could not read (DHCP failed?) or something negative to that effect. Anyways..when I finally booted into Ubuntu I had no connection,,and it was as if the cable was not connected. Conky indicated no network activity., the network icon indicated looking for a connection was in place,,and when i did network tools the options where greyed out.


I believe this is probably a BIOS issue,,since it all happened before Grub even came on, and in my xp dual boot ther was no connection either.  

Things I tried:
-made sure the cable was all the way in the jack
-ctrl S changing network boot protocol from RPL to PXE
-looked in Bios for something to change but didnt see anything. 
-I switched pci slots
-I reinstalled the old card (one I am on now) which works but is slow
-searched google for a solution
-searched intel's support page for a solution
-repeated all of the above


My BIOS is American Megetrends

If anyone has any Ideas I would appreciate it,,

---

### Post by SteveNorman on 2008-06-27
I'll throw a free concert while I wait


:guitar::-({|=:-\"









=D>=D>=D>=D>=D>

---

### Post by SteveNorman on 2008-06-27
I put the new (non-working) card back in today and ran lspci and ifconfig
ifconfig:
```
eth1      Link encap:Ethernet  HWaddr 00:19:21:28:a6:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xdead 

eth2      Link encap:Ethernet  HWaddr 00:1b:21:1c:e0:f7  
          inet6 addr: fe80::21b:21ff:fe1c:e0f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:233864 (228.3 KB)  TX bytes:10071 (9.8 KB)
          Base address:0xbc00 Memory:f9fc0000-f9fe0000 

eth2:avahi Link encap:Ethernet  HWaddr 00:1b:21:1c:e0:f7  
          inet addr:169.254.9.5  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Base address:0xbc00 Memory:f9fc0000-f9fe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55035 (53.7 KB)  TX bytes:55035 (53.7 KB)

```
lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:08.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:09.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
```

---

### Post by SteveNorman on 2008-06-27
I put the new (non-working) card back in today and ran lspci and ifconfig
ifconfig:
```
eth1      Link encap:Ethernet  HWaddr 00:19:21:28:a6:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xdead 

eth2      Link encap:Ethernet  HWaddr 00:1b:21:1c:e0:f7  
          inet6 addr: fe80::21b:21ff:fe1c:e0f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:233864 (228.3 KB)  TX bytes:10071 (9.8 KB)
          Base address:0xbc00 Memory:f9fc0000-f9fe0000 

eth2:avahi Link encap:Ethernet  HWaddr 00:1b:21:1c:e0:f7  
          inet addr:169.254.9.5  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Base address:0xbc00 Memory:f9fc0000-f9fe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55035 (53.7 KB)  TX bytes:55035 (53.7 KB)

```
lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:08.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:09.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
```


If anyone sees anything let me know,,Still cant get online with that card.

BTW I enabled my integrated card in bios,,tho its never worked. Its the Intel on I want to work

---

### Post by lswb on 2008-06-28
The pre-grub message makes it appear that the new card for some reason is causing the system BIOS to try to do a network boot. After installing the card, try accessing system BIOS and checking boot device order, make sure your hard drive is listed before network.

---

### Post by SteveNorman on 2008-06-28
I didnt see anything in bios that looked like a boot option for the NIC. My boot option starts with my DVD drive. Since I do eventually boot into Ubuntu shouldnt I be able to get the card to work from here?

---

