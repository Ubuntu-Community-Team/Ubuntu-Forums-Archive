---
title: "[HP dv 2699ee]Broadcom and nVidia woos"
date: 2008-10-28
forum: Hardware
---

### Post by radopod on 2008-10-28
I love this product except that I am not being able to run the above two things, my Wifi and nVidia 8400GS Graphics card.

Broadcom I suppose has released a driver and I presume it has also been added to 8.04. I updated my system completely today but it still doesn't seem to work. :(

nVidia Drivers installation is reporting a 'Kernel Interface not found' error. Is there a way around this?

I have searched and searched for the better half of the day but whatever suggestions I find are pretty complex for a novice like me. Thanks for your replies in advance.

---

### Post by sergiom99 on 2008-10-28
please post the outputs of the following commands typed in a console shell:
lspci
lsusb

you could also check: [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by radopod on 2008-10-28
Here are the outputs as you requested

**With lspci**

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

**With lsusb**

```
Bus 007 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by radopod on 2008-10-28
I have an update guys! :D My first reactions about this community and software are WOW!!!

I have solved the display driver issue using EnvyNG! What a beautiful program designed by Alberto! WOW!!!

Now to get this Broadcom working. ;)

---

### Post by radopod on 2008-10-28
I had a look at the other thread sergiom99. I also had a look at the drivers readme earlier this afternoon before posting here but the instructions seemed tough for me to grab on day one in Ubuntu Land. I will give it a try again tomorrow.

What I want to know is if whether or not these drivers would be included as a default in 8.10? I read somewhere that they would be. If so would I still have to go through all these instructions to install it?

---

### Post by sergiom99 on 2008-10-29
sorry to say, but you have an Intel wireless card, not broadcom:

> 07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
search for this specific model in the forums and there surely is a solution.

As for the nvidia, they work out of the box since Hardy in my laptop.

---

