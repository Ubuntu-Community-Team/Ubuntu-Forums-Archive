---
title: "Ubuntu 7.10 problem in HP Pavilion DV6016ea.Please help me"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by Snake16 on 2008-02-14
Hi! Obviously im still a newbie when it comes to Linux world. But im trying to be atleast proficient in operating all or some of the linux distros.For all we know, its a Vista age for windoze user now but as for me, Vista GUI rocks but over-all it sucks! no offense for those vista user but that's the way I see it. I really preferred to use Linux than goin to Vista path.

Anyway, I successfully installed the Ubuntu 7.10 LiveCD in my HP Pavilion DV6016ea. I really love the user-friendliness of this distro not to mention the Gnome GUI. Okey, here's my concern about my newly installed Ubuntu 7.10 on my: 

HP Pavilion DV6016ea
AMD Turion 64x2 1.61 GHz
1024MB RAM
Geforce Go 7200 64MB (up to 256 MB shared)
Broadcom BCM4312 802.11a/b/g (rev.0)
Nvidia Chipset

After the LiveCD installation, I tried to enabled my graphic card using Restricted Drivers Manager GUI but the system always prompt with this message: “The software source for the package nvidia-glx-new is not enabled” I also followed(or not at all) every post in different Linux forums but still I can't figure it out how it works. I used the apt-get command to install the envy but nothing happenned. By the way I manually downloaded the envy installer. I think apt-get tries to access the internet for repositories. Is it possible to use apt-get with an off-line .deb file like for instance, I downloaded a particular .deb or .tar and save it in my hard drive, how can I install these offline files like in windoze XP – just download the setup.exe or .msi, fire it and installation done.. Please help me. Do I really need to connect to the internet using my new Ubuntu OS? If yes, how could I connect to the internet world by using a newly installed Ubuntu 7.10.How can I configure my ethernet card to connect to a DSL/broadband internet?

Heres my ifconfig:
eth2      Link encap:Ethernet  HWaddr 00:00:6C:2B:01:4E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4896 (4.7 KB)  TX bytes:4896 (4.7 KB)

How come that my ethernet card was identified as eth10 and not eth0? Does it mean there’s something wrong with the installation?Is it supposed to be eth0 all the time? And I also noticed that my Ethernet card ID name varies each time I restart my laptop and log in to ubuntu and issue an ifconfig. By the way Heres my ethtool eth10:

Settings for eth10
	Supported ports: [ MII ]
	Supported link modes:	10baseT/Half  10baseT/Full
			100baseT/Half  100baseT/Full
			1000baseT/Full
	Supports auto-negotiation: Yes
	Advertised link nodes:  	10baseT/Half  10baseT/Full
			100baseT/Half  100baseT/Full
			1000baseT/Full
	Advertised auto-negotiation: Yes
Speed: Unknown! (65535)
Duplex: Unknown (255)
Port: MII
PHYAD: 1
Transceiver: external
Auto-negotiation: on
Supports Wake-on: g
Wake-on: d
Link detected: no


And heres my lspci:
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


Also, in broadcom wireless card. when I enabled it says: “The software source for the package bcm43xx-fwcutter is not enabled.” I really dont know what to do.. extremely appreciated if anyone could help me or show me the right path for a complete guide or step-by-step procedure in installing all drivers of my HP pavilion laptop  using Ubuntu 7.10.
Lastly, 
1.	does anyone could help me or tell me a good (or better) CD/DVD burning software tool for Ubuntu?
2.	I noticed one annoying thing whenever I logged-in in my GNOME. There's always a pop-up message saying : Battery may be broken. Your battery has a very low capacity (38%), which means that it may be old or...is there any workaround to fix this issue?
3.	Ubuntu 7.10 wont recognize/detect my Imation USB flashdisk when I plugged/re-plugged it to my laptop.What could be cause of this and necessary workaround to fix this issue?

As always, thank you in advance for those who could help me with all my dilemmas...

Even though I face a lot of troubles using Ubuntu 7.10 as of this moment, still, Ubuntu Gutsy rocks!


P.S
Pardon me for a very long post… =)

---

### Post by DoctorMO on 2008-02-14
Hmm in order to use the restricted drivers manager you really need to be online. It's the way the concept was designed to work.

If you can get your computer online first (for instance by using ethernet instead of wifi) to download these packages.

The alternative is that you use an alternative computer to download the required debs and place them in your /var/cache/apt/archives/ which should negate the need to download the package.

---

