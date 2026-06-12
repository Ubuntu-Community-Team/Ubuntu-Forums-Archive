---
title: "extremely slow SATA speed"
date: 2010-11-14
forum: Hardware
---

### Post by miles916 on 2010-11-14
Hi everyone! 

ive searched around and found a few threads regarding this problem, but no suggested solutions help... 

i have 3 harddisks connected to my mobo thru sata. transfer speeds between them are cripplingly slow at around 5-10 MBps. 

now, if i boot from a live-cd i can move files around at around 80MBps, so i doubt theres anything wrong with the drives themselves... im assuming it has something to do with my sata controller

heres the output of lspci: 

```
user@pc:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Atheros Communications L1 Gigabit Ethernet (rev b0)
**03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)**
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
05:02.0 USB Controller: NEC Corporation USB (rev 41)
05:02.1 USB Controller: NEC Corporation USB (rev 41)
05:02.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
```im assuming the jmicron controller is causing some sort of problem, but i cant get rid of it because without it i cant seem to control my dvd drive (IDE)... 

does anyone have an idea to point me in the right direction? 

what ive tried:

[LIST]
[*]checked udma settings (all correct as far as i can tell)
[*]turned said jmicron controller off in bios - no change except my dvd drive disappears
[*]tried updating bios & jmicron controller - both newest versions
[/LIST]
any help would be greatly appreciated.

regards, 
M.

---

### Post by x-dexter-x on 2010-12-08
Hi all,
I don't have the solution but I've the same problem.
Perhaps, like me, the controller gave us this problem it's:
```
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
```And like you I've found few thread on this problem.
Everything I can do is to watch the time go hoping someone find a solution.:popcorn:
Really sad. :sad:

P.s. no change done in bios or config hardware from the 10.04 where all gone perfect and mine is a fresh install, not an upgrade.

---

### Post by miles916 on 2011-08-14
Hi everyone! 

just in case anyone is still experiencing this kind of issue, try taking a look at your power supply. for me, it seems that my PSU was just too weak (was ~450W) for all the hardware i had upgraded with over the years... after getting a new PSU with a higher wattage (800W) everything has been fine since. 

regards, M.

---

