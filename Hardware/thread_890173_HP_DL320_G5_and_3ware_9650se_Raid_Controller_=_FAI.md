---
title: "HP DL320 G5 and 3ware 9650se Raid Controller = FAIL"
date: 2008-08-14
forum: Hardware
---

### Post by z33k3r on 2008-08-14
I just wanted to make a post about the horrible experience I had this week with RAID controllers.

I recently purchased a nice new HP DL320 G5 server with the intent to create a nice little 1U caching/MySQL server. Performance doesn't need to be screaming so I chose to go with RAID1 for redundancy as the unit only has two HDD bays.

I purchased a nice little 3ware 9650SE as it met all my criteria; or so I thought. It had the PCI-E slot due to the 1U riser only having PCI-E. It also was an affordable option. In my last server, I had built a nice little RAID5 with a 3ware 9550SX and I have yet to have a hick-up on that one (knock on wood). So I went for the 3ware.

Apparently I didn't Google the server and controller combination as the HP DL320 G5 has an incompatibility issue with the 3ware 9650SE! The HP does not allocate enough memory to boot into the raid controller's BIOS. 

3ware says that it's HP's fault for not opening up the memory, but then HP says that it's 3ware's controller for requiring so much memory... AAAAAAAAAAAaaaaaaaaaaahhhhhh....

The point is that no where on the internet is a definable answer on whether the 3ware 9650SE is compatible with the HP DL320 G5 server. 

The answer is no. From the words of the 3ware support associate, "There is no solution as of yet for the incompatibility of the 3ware 9650SE RAID controller when paired with a HP DL320 G5 server."

---

### Post by z33k3r on 2008-08-15
Just a quick question. I am thinking of replacing this with an Areca 1210 RAID controller. Does anybody have any advice on whether this is a good or terrible choice?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816131003](http://www.newegg.com/Product/Product.aspx?Item=N82E16816131003)

> Model
Brand 	areca
Model 	ARC-1210
Specifications
Type 	SATA II
Internal Connectors 	Multi-layer SATA connector
Interface 	PCI-Express x8
Cache Memory 	256MB on-board DDR333 SDRAM with ECC protection
RAID 	RAID 0/1/1E/3/5 JBOD
Operating Systems Supported 	Windows 2000/XP (Scsiport Driver)
Windows Server 2003 (Scsiport Driver and Storport Driver)
Redhat Linuxand SuSE Linux
FreeBSD
Solaris 10x86
UnixWare 7.1.x
Netware 6.5
Windows Vista 	Works with Windows Vista
Features
Features 	IntelR IOP332 I/O processor
Write-through or write-back cache support
Support up to 4 SATA II drives
Multi-adapter support for large storage requirements
BIOS boot support for greater fault tolerance
BIOS PnP (plug and play) and BBS (BIOS boot specification) support

RAID Features:
Multiple RAID selection
Array roaming
Online RAID level/stripe size migration
Online RAID capacity expansion and RAID level migration simultaneously
Instant availability and background initialization
Automatic drive insertion/removal detection and rebuild
Greater than 2TB per volume set
Support S.M.A.R.T, NCQ and OOB Staggered Spin-up capable drives
Support spin down drivers when not in use to extend service life (MAID)

Monitors/Indicators:
System status indication through HDD activity/fault connector, LCD Connector and alarm buzzer
SMTP support email notification
SNMP support for remote notification
I2C Enclosure management ready
Packaging
Package Contents 	ARC-1210
User Manual
4 x SATA Cable
L-P Bracket
Other Accessary 

---

### Post by ahansen on 2008-09-11
I've been battling a problem with the HP e200 controller in my ML350G5 and found my way to the guy who has been writing kernel updates for HP controllers for the linux kernel.  I'm battling super slow write performance and he advised me to go with the P400 controller.  I haven't done it yet, but that's my plan.  Kinda stinks dropping $500, but its better than super slow systems...

---

### Post by z33k3r on 2008-09-12
> **z33k3r said:**
> Just a quick question. I am thinking of replacing this with an Areca 1210 RAID controller. Does anybody have any advice on whether this is a good or terrible choice?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816131003](http://www.newegg.com/Product/Product.aspx?Item=N82E16816131003)

Just to follow this thread up and bring closure to MY issue, the Areca installed without a hitch and my new server is *BLAZING *fast! Was able to boot up and directly build the RAID. Restarted with the server install and installed without even a blink! Money well spent... 

I used to be a 'build it on a budget with good performance' but now I can see the benefits of extra capitol in server builds.

:popcorn:

---

### Post by itmaccnt on 2009-01-12
I just wanted to thank you for your post. I had a similar problem building a machine with a number of boards in it, all of which had BIOS options involved. I plopped my 3Ware 8006-2LP in, and no BIOS options. My OS would see it, but no options during boot. I ended up going into my motherboard BIOS and switching my onboard ICH9 to ACPI instead of RAID, and that must have freed up enough memory for my 3Ware card to load its BIOS option. I won't go into all the avenues I tried while troubleshooting this issue, but needless to say, much time was spent. Just prior to finding your post, I had decided to keep a second machine just to run the RAID I had previously set up on the 3Ware card, and use the new one for only part of what I had wanted. You saved me.

Rock on

---

