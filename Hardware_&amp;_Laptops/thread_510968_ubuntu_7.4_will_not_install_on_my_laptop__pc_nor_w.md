---
title: "ubuntu 7.4 will not install on my laptop  pc nor will the live cd work. I have a HP P"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by VonBarter on 2007-07-27
ubuntu 7.4 will not install on my laptop  pc nor will the live cd work. I have a HP Pavilion dv6000 Please advise

OS Name	Microsoft® Windows Vista™ Home Premium	
Version	6.0.6000 Build 6000	
Other OS Description 	Not Available	
OS Manufacturer	Microsoft Corporation	
System Name	HP-PC	
System Manufacturer	Hewlett-Packard	
System Model	Pavilion dv6000 (RD167AV#ABA)	
System Type	X86-based PC	
Processor	AMD Turion(tm) 64 X2 Mobile Technology TL-60, 2000 Mhz, 2 Core(s), 2 Logical Processor(s)	
BIOS Version/Date	Hewlett-Packard F.38, 6/20/2007	
SMBIOS Version	2.4	
Windows Directory	C:\Windows	
System Directory	C:\Windows\system32	
Boot Device	\Device\HarddiskVolume1	
Locale	United States	
Hardware Abstraction Layer	Version = "6.0.6000.16386"	
User Name	HP-PC\Mark	
Time Zone	Eastern Daylight Time	
Total Physical Memory	2,046.00 MB	
Available Physical Memory	1.33 GB	
Total Virtual Memory	4.21 GB	
Available Virtual Memory	3.37 GB

---

### Post by cmonkey on 2007-07-27
Any specifics on error messages or where during boot up it fails would be useful (or necessary).

---

### Post by jcaveman on 2007-07-27
When booting from the live CD, on the boot option page hit F6 and add the boot option noapic.  HP DV6000 series with AMD processors tend to have a problem with APIC.

---

### Post by 99vadim on 2007-08-06
Try adding these commands to kernel in Grub: **iommu=off** and **noirqdebug**. I've got a similar dv6000 laptop with AMD 64X2 Turion and it works just fine for me. Previously I used **noapic**, but the command tended to freeze my computer.

---

