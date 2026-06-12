---
title: "Upgraded to 9.04 but wireless disconnects again and again"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by aakar on 2009-06-16
hey ,

i have upgaraded to ubuntu 9.04 from 8.10 , in the hope of better version, but in 9.04 i m facing a problem of being getting disconnected again and again , from wifi  , 

plz help me out !!
thnx

---

### Post by xir_ on 2009-06-16
what wireless card do you have?

post the output of ifconfig from the terminal.

:-)

---

### Post by aakar on 2009-06-16
eth0      Link encap:Ethernet  HWaddr 00:1b:24:af:ac:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40253 (40.2 KB)  TX bytes:40253 (40.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:60:f0:1c  
          inet addr:10.0.152.18  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21a:73ff:fe60:f01c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2795068 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:193104895 (193.1 MB)  TX bytes:9976045 (9.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-60-F0-1C-30-31-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



but i wifi use to wrk fine woth the previous version , ie 8.10

---

### Post by xir_ on 2009-06-16
The reason i ask is because it is possible that since the last release there has been a driver change for your [FONT=Arial]wireless card/dongle in the kernel.

post the output of 
[/FONT]```
lspci

```[FONT=Arial]

this show help us figure it out[/FONT]

---

### Post by PureLoneWolf on 2009-06-16
I had the exact same issue and had to follow this [http://ubuntulinuxhelp.com/speed-up-your-internet-connection-in-ubuntu-linux/](http://ubuntulinuxhelp.com/speed-up-your-internet-connection-in-ubuntu-linux/) to get it working properly.

---

### Post by aakar on 2009-06-16
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

---

### Post by xir_ on 2009-06-16
well one option to test to see if it it is the dirver is to install WICD, this is an alternative to network manager and has solved some similar broadcom problems for others 

[http://ubuntuforums.org/showpost.php?p=7151640&postcount=10](http://ubuntuforums.org/showpost.php?p=7151640&postcount=10)


the code you need to install is 

```
sudo apt-get install wicd
```and then launch the program and try to log in to your network.


Note: this will remove network manager so dont do this if there are any particular features u need, or if you are not comfortable with risking you connection. I have done this personally about 30 times and not had a problem, but just a warning.

---

### Post by aakar on 2009-06-17
i installed wicd when resulted in deletion on gnome-nm-applet, but when i ran it resulted in saying that a particular file is missing, so i reverted bck to gnome-nm-applet...i think  wicd wouldnt have wrk successfully..... can u suggest smthing else ...........plzzzz

---

### Post by aakar on 2009-06-17
hey xir .... i iwould like to tellu one thing more ....that the problem of disconnection continues on a particular network ,......the network @ home continues to connected , where as network @ college drop of connection  again and again

---

### Post by xir_ on 2009-06-17
ahh i have the same problem actually in my uni lab (different chipset though).


Is there any type of authentication for your college network, eg mac address check or a standard password sign in?


Edit: btw there is a wicd guide here 

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

there are a couple of trouble shooting tips.

---

