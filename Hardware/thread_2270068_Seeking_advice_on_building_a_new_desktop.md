---
title: "Seeking advice on building a new desktop"
date: 2015-03-20
forum: Hardware
---

### Post by satimis on 2015-03-20
Hi all,

I'm prepared to upgrade my current desktop which is running Oralce VirtualBox.  This box is still running without much problem but the motherboard is only with 2 SATA connectors working.


Configuration of the current box
====================
120G SSD - for running OS - Ubuntu 14.04
WD Black label - 1 TB HD for installing VM

RAM - 8GB:
$ free -m```

             total       used       free     shared    buffers     cached
Mem:          7753       1626       6126          0         75        646
-/+ buffers/cache:        904       6849
Swap:         4979          0       4979

```

CPU: AMD
$ sudo lshw -class processor```

  *-cpu                   
       description: CPU
       product: AMD Phenom(tm) II X4 955 Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: AMD Phenom(tm) II X4 955 Processor
       serial: To Be Filled By O.E.M.
       slot: AM3
       size: 3200MHz
       capacity: 3200MHz
       width: 64 bits
       clock: 200MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
       configuration: cores=4 enabledcores=4 threads=4

```

ASUS Motherboard:
$ sudo dmidecode -t 2```

# dmidecode 2.11
SMBIOS 2.5 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer INC.
	Product Name: M4A78T-E
	Version: Rev 1.xx
	Serial Number: MS1C97B06200284
	Asset Tag: To Be Filled By O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To Be Filled By O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

```


My plan for upgrade:-
============
Motherboard:
ASUS M5A97 LE R2.0 AMD 970,DDR3,USB3.0,SATA3 6Gb/s,ATX M/B	655
[http://www.asus.com/Motherboards/M5A97_R20/](http://www.asus.com/Motherboards/M5A97_R20/)

CPU:
AMD 8-Core FX-8320 3.5GHz/16M CPU [AM3+] FD8320FRHKBOX [Black Edition]

RAM
I'll retain the old 8G RAM if it can be used?

Video Card:
ASUS DI-E730SL2 GT730-SL-2GD3-BRK GT730 2GB DDR3
I don't game.

Hard Drive
<SSD>Transcend SSD370 1TB 2.5" SATA 3 6Gb/s SSD 7mm TS1TSSD370


Please advise.  Any other suggestion will be appreciated.  Thanks in advance.

The reason for me sticking on ASUS components is "They are trouble FREE".  I have been using GIGABYTE motherboard and video card before but broken down after one year.

Remark:
I have no preset budget but it is NOT my wish using a 10-ton lorry to carry 1-ton goods.

Regards
satimis

---

### Post by dino99 on 2015-03-20
why are you glancing for new hardware ?  Your actual one can easily enough support virtualbox installation

---

### Post by satimis on 2015-03-20
> **9d9 said:**
> why are you glancing for new hardware ?  Your actual one can easily enough support virtualbox installation
Thanks for your advice and link.

Your are right.  VirtualBox works on my current desktop without problem.  My problem is "the motherboard only with 2 SATA connectors working".  I need 4 SATA connectors;

one for connecting 120G SSD (for OS)
one for connecting 1TB WD HD, Black label (for installing/running VMs)
one for DVD Writer
one for another Seagate 640G HD, for storage purpose.

To purchase a new motherboard to replace the defective one?  

Besides I expect to install a 1TB SSD to replace the existing 120G SSD and the 1TB WD HD.

Regards
satimis

---

### Post by dino99 on 2015-03-20
there is also the choice to select an additional card which provide these required sata ports (either sata3, sata6, msata) and plugged into a pci port

that way you does not need new mobo, new ram, new cpu, ...

---

### Post by satimis on 2015-03-20
> **9d9 said:**
> there is also the choice to select an additional card which provide these required sata ports (either sata3, sata6, msata) and plugged into a pci port

that way you does not need new mobo, new ram, new cpu, ...

Hi,

Whether to purchase a SATA3 Add-on Card?

Example:
[http://www.biostar.com.tw/app/en/event/sata3_card/](http://www.biostar.com.tw/app/en/event/sata3_card/)

Thanks

Actually the existing motherboard came with 4 SATA connectors but 2 became defective. not working

Furthermore for the new 1TB SSD do I need another new SATA addon card?  If YES I will buy a new SATA3 addon card for it and use the 2 working SATA connectors for DVD Writer and the storage HD respectively.

Regards
satimis

---

### Post by dino99 on 2015-03-20
there is lot of formats and ports; google around to document (pci1x pci2x m2)

for example: [http://www.ebay.com/bhp/pci-sata-card](http://www.ebay.com/bhp/pci-sata-card)  (but some are oldish sata, not 3 or 6)
you might find store on line in your country i suppose; and choose reputable make.

---

### Post by satimis on 2015-03-20
> **9d9 said:**
> there is lot of formats and ports; google around to document (pci1x pci2x m2)

for example: [http://www.ebay.com/bhp/pci-sata-card](http://www.ebay.com/bhp/pci-sata-card)  (but some are oldish sata, not 3 or 6)
you might find store on line in your country i suppose; and choose reputable make.
Just googling a while most the cards found are with external ports.  However I need internal ports.  I think I have to shop in person to find out the addon card for my use.

satimis

---

