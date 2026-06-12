---
title: "Is My System Compatible?"
date: 2010-06-01
forum: Hardware
---

### Post by tomihasa on 2010-06-01
How do I know if my system is compatible with Wubi 10.04 (I have also tried installing Ubuntu 10.04 LTS Desktop Edition, Fedora 13 Desktop Edition, and Mandriva Linux One 2008/2010 with or without Windows 2000 SP4 and I always end up with the grub or grub rescue prompt)? My system info for my approximately 10 years old PC (it has RAID functionality, but I've never used it. BIOS was created in 2001, but there are no new updates from ABIT for it.):

Motherboard: ABIT KT7A-RAID, VIA KT133A, Socket A, RAID.
Power supply: Silver Power SP-400P1B, 400 W.
Case: MaxPoint Miditower, ATX.
Processor: AMD K7 1400 MHz Thunderbird 256 KB Socket A 266.
Memory: 768 MB SDRAM, PC-133 MHz.
Video card: Matrox Millenium G550 32 MB DDRAM Dual (AGP slot).
Hard drive: Seagate Barracuda 40.8 GB UATA/100, 7200 rpm (IDE slot).
Disk drive: Sony floppy drive 1.44 MB 3.5".
Sound card: Sound Blaster Live! Player 5.1 (PCI slot).
Monitor: LG Flatron 995FT 19".
Keyboard: Microsoft Natural Keyboard Pro.
Mouse: Logitech Mini Wheel Mouse.
Network adapter: A-Link NA110HR (10/100 MB, based on Realtek chipset) (PCI slot).
ADSL modem: ZyXEL Prestige 660R-61, ADSL 2+ (external).
CD-RW drive: LG CD-RW 12x/8x/32x (IDE slot).

---

### Post by tomihasa on 2010-06-03
Problem solved. [Legacy GRUB Page]("http://members.iinet.net.au/~herman546/p15.html") gave me a clue: Windows may install another copy of Windows instead of a clean install. So I used my old MS-DOS 6 installation floppy disk to format my hard drive, because my various Linux distros didn't understand my hard drive maybe because how Windows formats and creates partitions to hard disks. Then I tried to install Mandriva, which still didn't work. Last, I tried installing Fedora 13 and it worked!

---

