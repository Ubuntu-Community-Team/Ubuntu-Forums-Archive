---
title: "How to check attached PCI devices - post-system crash"
date: 2008-06-05
forum: Hardware
---

### Post by gk_jam on 2008-06-05
Hi all,

So I live in Virginia and got hit by the storms yesterday which took out power and thus pulled the power on my Ubuntu PC.

Now that it's come back up, the wireless card doesn't seem to be recognized. Is there a way to see which attached PCI devices are recognized by the OS? I looked for "Hardware Devices" or "Device Manager" in the System->Preferences and System->Admin menus but didn't find anything.

ifconfig doesn't list my ath0 wireless device. Also, the restricted drivers manager says the Atheros driver is installed but not in use. I'm trying to determine if my wireless card is fried or not, is there a definitive way to tell?

Also, may or may not be related but for full disclosure, I had just installed the new kernel update but not restarted when the power went. So my post-power outage startup was the first since the new kernel update.

Help much appreciated!

---

### Post by lisati on 2008-06-05
Try in the terminal:
```
lspci
```

Hope that helps.

---

### Post by gk_jam on 2008-06-05
Thanks for that tip. Using "lspci" amongst other entries I see:

```

01:07.0 Ethernet controller: Atheros Communication Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

```

I am guessing that is my wireless card. So Ubuntu can see it then, but not use it? Could this still be a hardware issue, or are there more diagnostics I can try in software?

In the Network Setting dialog window, I don't even see a wireless connection listed.

---

### Post by halw on 2008-06-06
What you listed looks to be your systems built-in ethernet controller.

Here are the lines pertaining to ethernet & wireless controllers I get when I execute lspci...

```
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
```

The first is the built-in ethernet controller. Second entry is my wireless pci card.

Maybe if you list the entire result of lspci and the specs on your system we could help a bit more.

---

### Post by gk_jam on 2008-06-06
Ok, here is the full lspci output. Is any of these a wireless card?

```

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
01:09.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)

```

I have two ethernet ports on the back of my PC (1 Gigabit and one not), plus a wireless card. Unfortunately I don't remember the brand/model of the wireless card, it's been a while.

---

### Post by halw on 2008-06-06
Do 'ifconfig' and 'iwconfig' from the terminal and post the results of both.

Also, is your system a desktop or laptop?

---

### Post by NullHead on 2008-06-06
Well your new kernel is automatically selected by default on startup. If you compiled madwifi then you'll need to re-compile it to get your ath_pci to modprobe with out errors. I would re-comfigure&&make it and see if that works. 

[http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz](http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz)

---

### Post by gk_jam on 2008-06-06
My system is a desktop, not a laptop (I hope this is the right forum, it's hardware though not laptop hardware). Here is the output of ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:14:85:04:af:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:14:85:04:af:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth0:avahi Link encap:Ethernet  HWaddr 00:14:85:04:af:e7  
          inet addr:169.254.8.106  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104068 (101.6 KB)  TX bytes:104068 (101.6 KB)

```

and iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

```

I am not using madwifi drivers so I don't think that's the issue. My wireless card used to work "as-is" with the Atheros restricted drivers installed. The drivers are still installed, but now they say "not in use".

---

### Post by NullHead on 2008-06-06
> **gk_jam said:**
> My system is a desktop, not a laptop (I hope this is the right forum, it's hardware though not laptop hardware). Here is the output of ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:14:85:04:af:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:14:85:04:af:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth0:avahi Link encap:Ethernet  HWaddr 00:14:85:04:af:e7  
          inet addr:169.254.8.106  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104068 (101.6 KB)  TX bytes:104068 (101.6 KB)

```

and iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

```

I am not using madwifi drivers so I don't think that's the issue. My wireless card used to work "as-is" with the Atheros restricted drivers installed. The drivers are still installed, but now they say "not in use".

That is actually the madwifi driver. You should uninstall the restricted driver from the restricted-drivers-manager and re-install it again. If that fails run this command and attach the dmesg_out.txt that the command will generate. ```
dmesg >> dmesg_out.txt
```

---

### Post by gk_jam on 2008-06-07
So since I really haven't made many changes to be Hardy install and I have a separate /home partition, I just reinstalled Hardy and all my stuff is working again. As you suggested, it was most likely a software issue with the drivers rather than hardware. Thanks!

---

