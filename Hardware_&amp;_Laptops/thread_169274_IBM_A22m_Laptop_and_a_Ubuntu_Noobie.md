---
title: "IBM A22m Laptop and a Ubuntu Noobie"
date: 2006-05-02
forum: Hardware &amp; Laptops
---

### Post by everett3rd on 2006-05-02
I am making the switch to Ubuntu on all my personal equipment.

My Desktop and my MAME machine installed smoothly with Zero hardware problems.

My IBM A22m Laptop was also a smooth install with One exception.
Wireless networking.

I have a Linksys WPC54G Ver 4 Wireless card and a WPC11 Ver 4.
Both cards work fine with XP.

I have been working on this for about a week now.
I have tried ndiswrapper using 3-4 how-to I found here in the forums.
The GUI for ndiswrapper as well. The GUI tells me the driver is installed but the hardware is not present even though I can see the card in the device manager.

I'll even go and buy a card that works at this point.

The built in NIC works fine....but my wife does not like me running the 100ft ethernet cable all over the apartment when I want to work. :rolleyes: 

Any help would be great.

Is there a Wireless NIC that just works?
Is there something I have to do with the PCMCIA slots on this Laptop?

Below is my Laptop hardware configuration.
Thanks for your time.
--------------------------------------
System Name	LAPTOP-A22M
System Manufacturer	IBM
System Model	2628TTU
System Type	X86-based PC
Processor	x86 Family 6 Model 8 Stepping 10 GenuineIntel ~996 Mhz
BIOS Version/Date	IBM KXET29WW (1.03d), 3/21/2001
SMBIOS Version	2.3
Total Physical Memory	256.00 MB
Available Physical Memory	54.53 MB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB
--------------------------------------------------------------------
Name	[00000001] Intel(R) PRO/100 SP Mobile Combo Adapter
Adapter Type	Not Available
Product Type	Intel(R) PRO/100 SP Mobile Combo Adapter
Installed	Yes
PNP Device ID	PCI\VEN_8086&DEV_1229&SUBSYS_22058086&REV_0C\3&61AAA01&0&18
Last Reset	5/2/2006 7:46 AM
Index	1
Service Name	E100B
IP Address	Not Available
IP Subnet	Not Available
Default IP Gateway	Not Available
DHCP Enabled	Yes
DHCP Server	Not Available
DHCP Lease Expires	Not Available
DHCP Lease Obtained	Not Available
MAC Address	Not Available
--------------------------------------------------------------------
Name	[00000011] Wireless-G Notebook Adapter ver.4.0
Adapter Type	Ethernet 802.3
Product Type	Wireless-G Notebook Adapter ver.4.0
Installed	Yes
PNP Device ID	PCI\VEN_17FE&DEV_2220&SUBSYS_00291737&REV_00\4&11988572&0&0011
Last Reset	5/2/2006 7:46 AM
Index	11
Service Name	IPN2220
IP Address	192.168.1.90
IP Subnet	255.255.255.0
Default IP Gateway	192.168.1.1
DHCP Enabled	Yes
DHCP Server	192.168.1.1
DHCP Lease Expires	5/3/2006 7:47 AM
DHCP Lease Obtained	5/2/2006 7:47 AM
MAC Address	00:0F:66:B9:A4: D1
I/O Port	0x0000FAE0-0x0000FAFF
Memory Address	0xFFDFE7E0-0xFFDFE7FF
Memory Address	0xFFDFE800-0xFFDFEFFF
IRQ Channel	IRQ 11
------------------------------------------------------------------------
Description	Disk drive
Manufacturer	(Standard disk drives)
Model	IC25N030ATDA04-0
Bytes/Sector	512
Media Loaded	Yes
Media Type	Fixed&#x0009;hard disk media
Partitions	3
Sectors/Track	63
Size	27.95 GB (30,005,821,440 bytes)
Total Cylinders	3,876
Total Sectors	58,605,120
Total Tracks	930,240
Tracks/Cylinder	240

Windows Partition
Partition	Disk #0, Partition #0
Partition Size	20.68 GB (22,208,223,744 bytes)
Partition Starting Offset	32,256 bytes

Ubuntu Partition
Partition	Disk #0, Partition #1
Partition Size	6.93 GB (7,443,878,400 bytes)
Partition Starting Offset	22,208,256,000 bytes

IBM Partition
Partition	Disk #0, Partition #2
Partition Size	337.30 MB (353,687,040 bytes)
Partition Starting Offset	29,652,134,400 bytes

---

### Post by bugme on 2006-05-02
Please provide a link to the how-to's so we can help you more accurately on the steps of the install.
Thanks

---

### Post by mips on 2006-05-02
[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)
[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)

---

### Post by everett3rd on 2006-05-03
Well....I feel like a fool....life goes so much better when you use the right driver. I have just moved and couldn't find the CD for my g card. I downloaded drivers from linksys and that is what I had been beating my head on for the last week. ](*,) 

I found the CD the card shipped with last night while unpacking a box....tried it, using ndiswrapper and the gui utility mentioned elswhere in this forum.

The card seems to be working fine, but I cannot associate with my Linksys AP.

The essid is not broadcast and it is using 64bit WEP.
I have to use 64bit becuase that is all my PDA will do (it's old)

I turned off all the security on the AP for a while and I can see it just fine form the laptop but I cannot get a DHCP address.
Also I cannot connect to the half dozen or so non-secure AP in my apartment building. I can see them noe though.

Any pointers would be great. 
I see the light at the end of the tunnel but I have 2 left feet...

Everett

---

### Post by everett3rd on 2006-05-05
After much ](*,) I have decided to solve this problem the old fashioned way.

I am going to throw some money at it.

After doing some research here in the forums and on the Wireless Hardware compatibility list: [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

While cross referenceing that with the stocks at Best Buy, CompUSA and MicroCenter I have decided to get a NETGEAR WG511T Wireless Card.

I will post the result on this thread and the this one too: [http://ubuntuforums.org/showthread.php?t=38972&pp=10](http://ubuntuforums.org/showthread.php?t=38972&pp=10)

---

### Post by mips on 2006-05-05
[QUOTE=everett3rd]After much ](*,) I have decided to solve this problem the old fashioned way.

I am going to throw some money at it.
[/QUOTE]

I suppose that's one way to skin a cat ;)

---

### Post by everett3rd on 2006-05-06
Problem solved.

I purchased the NETGEAR WG511T at CompUSA and did a clean install of Breezy (just incase I messed something up trying to get the other cards working)

The card worked out of the box. Just had to add the MAC address of the new card to my routers allowed list.

I can now go 100% ubuntu on my laptop. :D

---

