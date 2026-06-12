---
title: "Can PCIe 4.0 display card work on PCIe 3.0 motherboard"
date: 2023-09-24
forum: Hardware
---

### Post by satimis on 2023-09-24
Hi all,

Just purchased a new GIGABYTE GeForce RTX 3050 WINDFORCE OC8GB GDDR6 display card, PCIe 4.0.  It can't work on PCIe 3.0 motherboard.  I tested it, no signal output on both DP and HDMI ports

Motherboard:
ASUSTeK COMPUTER INC.
PRIME X570-P
Version: Rev X.0x

Is there anyway to make it works on PCIe 3.0 motherboard?  Please advise.

Thanks in advance.

---

### Post by Autodave on 2023-09-24
From what I understand, it should just work albeit at 3.0 standards.  Did you get the extra power connections connected?  What drivers, if any, for your previous card did you install?

---

### Post by #&amp;thj^% on 2023-09-24
According to the specs on the MB
```
Expansion Slots:	3x PCIe 4.0 x16 slots (x16/x0/x0 or x8/x8/x0 or x8/x4/x4)
3x PCIe 4.0 x1 slots 
```
If this is your Mother Board: [https://www.techpowerup.com/review/asus-prime-x570-pro/](https://www.techpowerup.com/review/asus-prime-x570-pro/)

---

### Post by satimis on 2023-09-25
> **1fallen said:**
> According to the specs on the MB
```
Expansion Slots:	3x PCIe 4.0 x16 slots (x16/x0/x0 or x8/x8/x0 or x8/x4/x4)
3x PCIe 4.0 x1 slots 
```
If this is your Mother Board: [https://www.techpowerup.com/review/asus-prime-x570-pro/](https://www.techpowerup.com/review/asus-prime-x570-pro/)

Hi 1fallen,

1)
Yes.

$ sudo dmidecode -t 2```

[sudo] password for satimis: 
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: ASUSTeK COMPUTER INC.
        Product Name: PRIME X570-P
        Version: Rev X.0x
        Serial Number: 190753869002923
        Asset Tag: Default string
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: Default string
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0

```

2)
Performed following test;

Install the MSI PCIe 3.0 display card of my spare PC to the daily working PC
MSI graphic card V292 R1
Model: MS V385

Connect to DP port

It works without problem
-> booting to grup menu -> starting Ubuntu 22.04 desktop

lspci | grep VGA```

01:00.0 VGA compatible controller: NVIDIA Corporation TU116 [GeForce GTX 1650 SUPER] (rev a1)

```

3)
Tested the new Gigabyte Geforce RTX 3050 PCIe 4.0 display card in my spare PC, still having the same problem.

PC boots to a dark screen finally after starting grup menu
PC can boot to BIOS and I can make changes.

Please help how to find out and fix the problem of the new Gigabyte Geforce RTX 3050 PCIe 4.0 display card

Thanks in advance

---

### Post by satimis on 2023-09-25
Hi all,

I found out the cause of problem, PCIe 4.0 graphic card unable to work on PCIe 3.0 slot of motherboard.  **[COLOR="#FF0000"]It works without problem !!![/COLOR]**

My Ubuntu 22.04 desktop is running on a PCIe Nvme 3.0 SSD.  This is the cause making PCIe 4.0 graphic card unable to work.

[B][COLOR="#FF0000"]Following OS are also running on this PC.
1) Windows 10 on STAT6 SSD

2) another Ubuntu 22.04 desktop on SATA6 SSD
[/COLOR][/B]

I just checked them.  PCIe 4.0 graphic card works on both of them without problem.  **[COLOR="#FF0000"]I'm now replying this thread on 2) above.[/COLOR]**

**[COLOR="#FF0000"]Is there any way to solve the problem, PCIe 4.0 graphic card unable to work on PCIe Nvme 3.0 SSD ?[/COLOR]**

I won't inject further effort on my spare PC because I won't install PCIe 4.0 graphic card on it.

Regards

---

