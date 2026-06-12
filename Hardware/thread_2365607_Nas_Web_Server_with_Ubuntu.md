---
title: "Nas Web Server with Ubuntu"
date: 2017-07-08
forum: Hardware
---

### Post by venteens on 2017-07-08
Hi!

I have a few questions regarding building websites with a Nas Web Server using Ubuntu.

1. I am going to move 5 websites (01 ecommerce and 4 wordpress blogs) with approx. 150,000 visitors/month to a VPS home business.
I am interested in a Nas Web server for their  Raid Configurations, backups, recovery functions, hot plug, Lan On Wake, Power Auto ON, etc.
 
2. Does Nas Web Server will be suitable for a productive web server?
I want to take complete control of the system with Ubuntu.

3. Please guide me on the best productive home server machine.

I am interested in this Nas models (follow the links):

[Netgear ReadyNAS 626X]("http://www.netgear.com/business/products/storage/readynas/RN626X.aspx")

[Qnap TVS-882ST3]("https://www.qnap.com/en/product/model.php?II=272")

*My Build Objectives:
-Low power consumption
-Silent operation
-Generate little heat
-Small form factor
-Backup ON
-Powered on and running 24/7.


Processor: Intel Quad Core 2.4GHz or +
System Memory: 8 GB DDR4 with ECC
CPU Architecture: 64bit
Operating System: Linux - Ubuntu
No. of Bays: 4
Internal Maximum (assume 10TB hard drives):40TB
Hot Swappable Drives
Drive Types Supported: SATA/SSD 2.5" or 3.5"
RAID: Automatic RAID configuration
RAID controller: 8 port.
Hardware RAID 0 / 1 / 5 / 10
Hot Plug
Wake on LAN
Power Auto ON
Port: USB (1) USB3.0 front,(2) USB3.0 rear
Headphone,mic×1
HDMI 1.4a×1
VGA Port×1
Intel Gigabit LAN Ports: 2 
  10Gbps LAN Optical SFP+: 0
  10Gbps LAN Copper 10GBase-T: 2
Internal Audio:6 channel ALC662 chipset
Sound Level: 35db
Power supply: Input:100V~240V, 50/60Hz internal 200W
Power Consumption: 29W
Environment Temperature
 

Thank you in advance,

Warm regards!

---

### Post by TheFu on 2017-07-08
No.  Just no.

Please don't do this.  

Use a NAS for storage on a LAN, never over the internet.  They just don't have the needed security.  Those devices come with a specialized OS designed to be used on a LAN, not the internet.

Use a server for serving anything on the internet.  Something that has new updates daily would be best, like Ubuntu server. Patch the OS and applications weekly - php stuff - daily.

You can build a NAS from a standard PC and run Ubuntu server on it, but I wouldn't mix internal and external information on the same machine. Security needs to be layered.  Expect your web-server to be hacked and all data on the machine to be know to the world.

---

### Post by venteens on 2017-07-08
Thanks a lot!

---

