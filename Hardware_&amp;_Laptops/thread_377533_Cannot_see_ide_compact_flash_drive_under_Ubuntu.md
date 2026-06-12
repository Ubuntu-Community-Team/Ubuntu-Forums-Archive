---
title: "Cannot see ide compact flash drive under Ubuntu"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by jayant on 2007-03-06
Hello,

I have a computer with a 80GB SATA disk as the Primary disk on IDE 0 (so it's /dev/sda) and a 512MB compact flash as the Secondary disk on IDE 1 (so i expect it to be /dev/hdd). Currently on the 80GB SATA drive I have put Windows and Ubuntu 6.06 and they both work fine. When I boot under Windows I am able to see and use the Compact flash card. But when I am under linux there seems to be no trace of this device:confused::shock:. It is not listed in /dev/ and the dmesg ouput is pasted here.
> smacs@fastcompc30:~$ dmesg | grep ide
BIOS-provided physical RAM map:
CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
Boot video device is 0000:01:00.0
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
    ide0: BM-DMA at 0xb800-0xb807, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xb808-0xb80f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
ide1 at 0x170-0x177,0x376 on irq 15
Linux video capture interface: v2.00
smacs@fastcompc30:~$

Can someone give me an idea of what is wrong? Please let me know if you need more information and perhaps even how to get that information.

Thank you!

---

### Post by jayant on 2007-03-06
sorry. im silly and now everything works:). i found my cf drive under /dev/sdb

---

### Post by matt518000 on 2007-03-22
These units allow users to replace traditional hard drives with standard Compact Flash cards.
    There are some real nice bennefits to using compact flash in place of a regular hard drive.
    These include:
    - very low power consumption (less then 0.5W)
    - Fast startup, no spin up time, or USB bottleneck
    - high transfer rate
    - phisically very durable
    - compatibility with IDE drivers, nothing special needed
    - they are completely silent
    - The use commodity (cheap and plentiful) CF cards

    The frugal script works very nicely with CF, as it keeps disk writes to a minimum which is exactly what is needed to keep a compact flash card alive for a long time.

    Slap in a CF card with a myDSL image frugally installed and you have a virtually indestructible system which will be nearly hack proof. The combination of DSL, a mini-itx board running on an IDE/CF card and power it by a fanless power supply and you have a very efficient, very foolproof system which make virtually no noise.

    This might sound unprofessional of me, but to a Unix/Linux geek IDE to CF adaptors are just plain cool!
    
    to know about more ,pls visit [http://www.soarland.com](http://www.soarland.com). It is a Chinese menufactory that have a nice price.

---

