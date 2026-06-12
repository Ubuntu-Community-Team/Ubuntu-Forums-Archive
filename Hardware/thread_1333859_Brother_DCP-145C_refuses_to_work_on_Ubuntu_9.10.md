---
title: "Brother DCP-145C refuses to work on Ubuntu 9.10"
date: 2009-11-21
forum: Hardware
---

### Post by pzaw on 2009-11-21
Can someone help me find what is wrong with the Brother DCP-145C printer?
The printer is in sleep mode all the time. Printer works on xp machines.

First off to explain in detail.

I had a Ubuntu 8.xx samba file server, print server, DHCP server and internet gateway for about 8 months on my home network.

I had 2 network cards in it with Firestarter and DHCP server with Samba sharing files and printer/scanner.  The samba hard drives are mostly USB connected to a 5 port Balkin USB 2 PCI card.
The printer is a Brother DCP-145C using 

- dcp145ccupswrapper-1.1.2-2.i386.deb
- dcp145clpr-1.1.2-2.i386.deb
- brscan3-0.2.6-1.i386.deb
- brscan-skey-0.2.1-3.i386.deb

The Printer is plugged into the mother board USB port and NOT the Belkin.

I followed the instructions on the Brother web site and this forum and it worked straight away.
All was working and good with my world.

I even had the foresight to make notes of the steps/info that helped me set it up.
So this printer had been working with Ubuntu 8.XX for about 8 months.

BUT, recently I had problems with errors and Ubuntu 8.xx would go into check disk when first booted and then into command line and say something about sck or some such has corrected the filesystem.
This happened everytime I rebooted. (rebooted properly - by shutting down) My openoffice docs seem to get corrupted as well.

Anyway It was time, I thought, to change over the hard disk as this hard disk was about 4/5 years old.
So I did that but then I thought why put Ubuntu 8.04 back and then update etc when I could install 9.10 Desktop.

Wicked! Right?

So I proceded to waste one weekend trying to install 9.10 only to have it crash and burn before I realised that the problem was my nvidia graphics card.

so WHY change the Nvidia graphics card when I can change the computer with ATI graphics card so I did.

Now, everything worked ok. well almost.
I installed everything back from my notes and everything worked in 9.10, the Firewall, internet sharing, DHCP server, I even increased my file shares by 1TB.

Now for my present problem....

Everything is working except my Brother DCP-145C!, Cup says
DCP145C    DCP145C    usb://Brother/DCP-145C    Brother DCP-145C CUPS v1.1    Idle - "The printer is ready to print."

I can see it in cups as above but when I print the jobs are being "processed" and never gets printed.

like
DCP145C-9      Unsaved Document 1      nemo      12k      Unknown      processing since
Sun 22 Nov 2009 09:48:05 AM WST 


but the printer is in sleep mode and there is a printer icon on the desktop bar which says  something like DCP-145C may not be connected.

I HAVE followed the instructions to the letter. At least instructions I used for Ubuntu 8.xx. There maybe something with Ubuntu 9.10 that is stopping it from working. Of course I have changed the computers as well but as far as I can tell the USB ports are working electically.

So the nitty gritty of my internals is as follows.

dmesg | tail

[21959.956026] usb 5-2: device descriptor read/64, error -71
[21960.180020] usb 5-2: device descriptor read/64, error -71
[21960.396030] usb 5-2: new low speed USB device using uhci_hcd and address 67
[21960.516489] usb 5-2: device descriptor read/64, error -71
[21960.740068] usb 5-2: device descriptor read/64, error -71
[21960.956023] usb 5-2: new low speed USB device using uhci_hcd and address 68
[21961.364022] usb 5-2: device not accepting address 68, error -71
[21961.476026] usb 5-2: new low speed USB device using uhci_hcd and address 69
[21961.884032] usb 5-2: device not accepting address 69, error -71
[21961.884069] hub 5-0:1.0: unable to enumerate USB device on port 2

Seems to be something wrong here. Don't know what it means though

************************

and...

sudo lshw -businfo

Bus info          Device      Class      Description
====================================================
                              system     System Name
                              bus        P4PE
                              memory     64KiB BIOS
cpu@0                         processor  Intel(R) Pentium(R) 4 CPU 2.40GHz
                              memory     8KiB L1 cache
                              memory     512KiB L2 cache
                              memory     1536MiB System Memory
                              memory     1GiB DIMM DRAM Synchronous
                              memory     512MiB DIMM DRAM Synchronous
                              memory     DIMM DRAM Synchronous [empty]
pci@0000:00:00.0              bridge     82845G/GL[Brookdale-G]/GE/PE DRAM Contr
pci@0000:00:01.0              bridge     82845G/GL[Brookdale-G]/GE/PE Host-to-AG
pci@0000:01:00.0              display    RV350 AS [Radeon 9550]
pci@0000:01:00.1              display    RV350 AS [Radeon 9550] (Secondary)
pci@0000:00:1d.0              bus        82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US
pci@0000:00:1d.1              bus        82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US
pci@0000:00:1d.2              bus        82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US
pci@0000:00:1d.7              bus        82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Con
pci@0000:00:1e.0              bridge     82801 PCI Bridge
pci@0000:02:05.0  eth1        network    BCM4401 100Base-T
pci@0000:02:0a.0  eth0        network    RTL-8169 Gigabit Ethernet
pci@0000:02:0b.0              bus        USB
pci@0000:02:0b.1              bus        USB
pci@0000:02:0b.2              bus        USB 2.0
pci@0000:00:1f.0              bridge     82801DB/DBL (ICH4/ICH4-L) LPC Interface
pci@0000:00:1f.1  scsi0       storage    82801DB (ICH4) IDE Controller
scsi@0:0.0.0      /dev/sda    disk       120GB WDC WD1200JB-00G
scsi@0:0.0.0,1    /dev/sda1   volume     37GiB Linux filesystem partition
scsi@0:0.0.0,2    /dev/sda2   volume     69GiB Linux filesystem partition
scsi@0:0.0.0,3    /dev/sda3   volume     4800MiB Linux swap volume
scsi@0:0.1.0      /dev/sdb    disk       160GB ST3160021A
scsi@0:0.1.0,1    /dev/sdb1   volume     68GiB Linux filesystem partition
scsi@0:0.1.0,2    /dev/sdb2   volume     80GiB Linux filesystem partition
scsi@1:0.0.0      /dev/cdrom  disk       DVDRAM GSA-4160B
pci@0000:00:1f.3              bus        82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SM
usb@2:4           scsi2       storage   
scsi@2:0.0.0      /dev/sdc    disk       320GB 3200AAV External
scsi@2:0.0.0,1    /dev/sdc1   volume     102GiB Linux filesystem partition
scsi@2:0.0.0,2    /dev/sdc2   volume     195GiB Linux filesystem partition
usb@2:5           scsi3       storage   
scsi@3:0.0.0      /dev/sdd    disk       1TB Basics Desktop
scsi@3:0.0.0,1    /dev/sdd1   volume     439GiB Linux filesystem partition
scsi@3:0.0.0,2    /dev/sdd2   volume     434GiB Linux filesystem partition
scsi@3:0.0.0,3    /dev/sdd3   volume     57GiB Linux filesystem partition

**********************

dpkg  -l  |  grep  Brother
ii  brother-cups-wrapper-common          1.0.0-10-0ubuntu5                          Common files for Brother cups wrapper packages
ii  brscan-skey                          0.2.1-3                                    Brother Linux scanner S-KEY tool
ii  brscan3                              0.2.6-1                                    Brother Scanner Driver
ii  dcp145ccupswrapper                   1.1.2-2                                    Brother CUPS Inkjet Printer Definitions
ii  dcp145clpr                           1.1.2-2                                    Brother lpr Inkjet Printer Definitions


So can someone help me find what the hell is wrong with the Brother DCP-145C printer?
Is there anyway to get a response from the DCP-145C by other means?

Regards
Patrick

---

