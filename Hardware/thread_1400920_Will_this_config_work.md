---
title: "Will this config work?"
date: 2010-02-07
forum: Hardware
---

### Post by gnugu on 2010-02-07
Hi,
I'm planing to buy a new computer on which I would like to install 64-bit Ubuntu 9.10+.

Here is the config:
Processor: Intel Core I5 750 2.66GHz Quad Core Processor - 8MB L3 Cache, 95W, Socket 1156
Mainboard: Intel DP55WG Media Series ATX LGA1156 P55 2PCI-E16 2PCI-E1 2PCI 6SATA Motherboard
Video Card: Asus GeForce GT210 512MB DDR2 64BIT DVI PCIE HDMI HDCP Video Card

Can someone please tell me if the following two things will work?
1. Will the video card be well supported?
2. Will eSATA be hot swappable?

Thank you!

---

### Post by viper250 on 2010-02-07
this should work ok but your sata drives may need to be set to ide mode in the bios
I dont know if it will work hot swap though as I dont use 9.10

---

### Post by gnugu on 2010-02-07
> **viper250 said:**
> but your sata drives may need to be set to ide mode in the bios

Hi viper250,
thanks for your response.

What does the above mean and why should it be done? Thanks.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2010-02-07
The video card should be very-well supported and about the sata driver, it's that big of a deal with Ubuntu.
With some versions of windows you would have to force the hdd to run as ide or ahci and not as software raid, prior to installation.
For eSata I have no idea, but there are guides for that if you google search

---

### Post by gnugu on 2010-02-07
> **&#1057 said:**
> With some versions of windows you would have to force the hdd to run as ide or ahci and not as software raid, prior to installation.

&#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082;,
I'm confused. I want Ubuntu as OS and no RAID. One simple internal HDD and external HDD enclosure for backups preferred eSATA connection over USB.
I have old ASUS main board and it will not mount eSATA hot. Some people report that with new mother boards it works. Hence the question.

One twist, how would this mother board be supported?
MSI P55-CD53 ATX LGA1156 P55 DDR3 PCI-E16 3PCI-E1 3PCI SATA GBLAN DrMOS OC Genie Motherboard 

and is it better or worse than the one I posted originally?

Please forgive me, I'm more sw than hw guy :).

Thanks.

---

### Post by viper250 on 2010-02-07
the sata drive has a mode setting in the bios 
you would enter setup at boot select the drive and select the mode.
in some acer laptops the sata drive was set to ahci mode for windows vista this made its access speed faster for the os
but would cause problems trying to load any other os
in order to run any linux I had to set the sata mode to ide. then the drive was detected and installable

---

### Post by gnugu on 2010-02-07
> **viper250 said:**
> in order to run any linux I had to set the sata mode to ide. then the drive was detected and installable

Would this make the disks access slower?

---

