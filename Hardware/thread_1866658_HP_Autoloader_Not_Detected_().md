---
title: "HP Autoloader Not Detected (?)"
date: 2011-10-21
forum: Hardware
---

### Post by jaynv0i on 2011-10-21
I have an HP ProLiant Server with 2 642 SmartArray Cards and one 641 SmartArray card. My HP StorageWorks 1/8 G2 tape autoloader is connected to the 641 SmartArray card.  The machine is running Ubuntu 11.04.
 
When booting the machine, the LSILogin MPT BIOS detects the tape drive correctly, Ultrium 3 SCSI, 1x8 G2 Autoloader.
 
From dmesg, I can see all three of the controllers are being probed, but the tape drive never show up. Following is the output I thought was relevant from dmesg. If more information is needed, please let me know and I will post it.
[ 0.120907] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[ 1.323007] cciss 0000:02:01.0: cciss0: <0x46> at PCI 0000:02:01.0 IRQ 11 using DAC
[ 1.352832] cciss 0000:02:02.0: cciss1: <0x46> at PCI 0000:02:02.0 IRQ 3 using DAC
[ 1.452447] cciss 0000:05:02.0: cciss2: <0x46> at PCI 0000:05:02.0 IRQ 10 using DAC
 
Running cdrecord -scanbus shows only the DVD as being available.
scsibus0:
0,0,0 0) 'TSSTcorp' 'CDW/DVD TS-H492C' 'IB01' Removable CD-ROM
0,1,0 1) *
0,2,0 2) *
0,3,0 3) *
0,4,0 4) *
0,5,0 5) *
0,6,0 6) *
0,7,0 7) *
 
I think my tape drive is being recognized as a SCSI drive instead of a tape drive.
 
In order to make the external drive array work correctly, noapic and nolapic were added to the grub configuration file using the boot-repair utility.
 
I have added mpt_load="YES" to the /etc/modules file so the mpt module will be loaded when the system is booted. 
 
I have also checked the tape drive, and it is properly terminated.
 
Any suggestions would be greatly appreciated. Thank you, and I hope everyone has a nice weekend.
 
 
 
Jay

---

