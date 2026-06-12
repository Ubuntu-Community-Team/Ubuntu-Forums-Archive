---
title: "Laptop Modem Help"
date: 2006-09-20
forum: Hardware &amp; Laptops
---

### Post by jthomp86 on 2006-09-20
Hi all. First of all, I'm running xubuntu. I've gotten all my other hardware and everything set up. The only thing is, I have dial up and my modem is not recognized by xubuntu and I've been reading some tutorials and the setup seems confusing. I'm not a total noob when it comes to linux, but I've been unable to set up my modem successfuly as of yet with ubuntu. I have downloaded scanModem and here is the output from some of the files. Perhaps you all can steer me in the right direction.

> From: ModemData
--------------------------  System information ----------------------------
 Ubuntu 6.06.1 LTS 
Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
 scanModem update of:  2006_September_20


USB modem not detected by lsusb

 Modem or host audio card candidates have firmware information:
 PCI ID     Subsystem  Name
 ---------- ---------  -----------------
 10de:00d9  103c:006d  Modem: nVidia Corporation: Unknown device 00d9 
 == Bootup Disablement problem ==
       [17179570.632000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179570.632000] **** SET: Misaligned resource pointer: df9752c2 Type 07 Len 0
[17179570.636000] ACPI: PCI Interrupt Link [LMCI] enabled at IRQ 22
[17179570.636000] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [LMCI] -> GSI 22 (level, low) -> IRQ 193
[17179570.636000] ACPI: PCI interrupt for device 0000:00:06.1 disabled
[17179570.636000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.636000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
 ================================


> from scanout.0000:00:06.1
-----------------------------------------
PCIDEV=10de:00d9
CLASS="Class 0703: 10de:00d9"
NAME="Modem: nVidia Corporation: Unknown device 00d9 "
Vendor=10de
Device=00d9
SUBSYS=103c:006d
SUBNAME=" Hewlett-Packard Company: Unknown device 006d"
SUBven=103c
IRQ=193
Test="./scanModem test 10de:00d9 103c:006d"
SOFT=10de:00d9
SLMODEMD_DEVICE=modem:1
PORT="modem:1"
Driver=snd-intel8x0m
DRIVER_=snd_intel8x0m
KDRIVER=SND_NTEL8X0M
MPLACE=


Any ideas?

---

