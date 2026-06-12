---
title: "Harddrive and administrative problems"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by Nemooo on 2008-02-20
First of I'd like to state, that I'm very happy with Ubuntu, there's just a few things I can't figure out.

1) My computer has two harddisks. One with 250 GB and another small harddisk on 40 GB. When I installed, I chose to use the big harddisk for Ubuntu (before used for Windows) believing, that I'd be able to acces the other harddisk via Ubuntu as it contains documents, pictures etc.

I can't seem to find the other harddisk, though. Why and how can I "get it back"?

2) How do I get administrative rights to edit files such as /etc/X11/xorg.conf? When I try to edit it, it says:

"You do not have the permissions necessary to save the file"


Thanks in advance

---

### Post by Yellow Pasque on 2008-02-20
1) Run some commands for us:
```
sudo lshw -businfo -C disk
sudo fdisk -l
```

To answer 2), use the sudo qualifier in front of the command, e.g.
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Nemooo on 2008-02-20
1)sudo lshw -businfo -C disk gives me:

```
Bus info          Device      Class       Description
=====================================================
scsi@0:0.0.0      /dev/cdrom  disk        DVD+-RW GSA-H21N
scsi@2:0.0.0      /dev/sda    disk        232GB SAMSUNG SP2504C
scsi@7:0.0.0      /dev/sdb    disk        USB   HS-CF Card
                  /dev/sdb    disk        
scsi@7:0.0.1      /dev/sdc    disk        USB   HS-xD/SM
                  /dev/sdc    disk        
scsi@7:0.0.2      /dev/sdd    disk        USB   HS-MS Card
                  /dev/sdd    disk        
scsi@7:0.0.3      /dev/sde    disk        USB   HS-SD Card
                  /dev/sde    disk
```

And sudo fdisk -l:

```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d2ffbfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30017   241111521   83  Linux
/dev/sda2           30018       30394     3028252+   5  Extended
/dev/sda5           30018       30394     3028221   82  Linux swap / Solaris
```

2) Works like a charm :)

---

### Post by Yellow Pasque on 2008-02-20
Hmm, lshw isn't picking it up. Are you sure the drive is connected properly and visible in the BIOS? Is it a PATA or SATA drive?

Can you give us some specs on your system (preferably the motherboard if you know what kind it is) or run:
```
sudo update-pciids; lspci
sudo dmidecode -t baseboard
```

---

### Post by Nemooo on 2008-02-20
I think it's a SATA drive, but not sure. How do I check if it's visible in the BIOS?

sudo update-pciids; lspci:

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)
```

sudo dmidecode -t baseboard:

```
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0200, DMI type 2, 8 bytes
Base Board Information
        Manufacturer: Dell Inc.          
        Product Name: 0FJ030
        Version:    
        Serial Number: ..CN7082168GJ00I.

Handle 0x0A02, DMI type 10, 6 bytes
On Board Device Information
        Type: Ethernet
        Status: Enabled
        Description: Intel PRO/100 VE Network Connections

Handle 0x0A03, DMI type 10, 6 bytes
On Board Device Information
        Type: Sound
        Status: Enabled
        Description: Intel(R) High Definition Audio Controller
```

I appreciate your help.

---

### Post by Yellow Pasque on 2008-02-20
When your computer first starts, you'll have to press a key to enter the BIOS setup. Probably 'Del' or F1. Every BIOS is different, but you should be able to poke around in there and find a listing of your disks. Make sure the BIOS sees the 40GB disk.

Was the 40GB drive the one that came with your PC? Do you know what model Dell it is?

---

### Post by Nemooo on 2008-02-20
I'll take a look at the BIOS. It's a Dimension 9150. Tell me if you need more specifications.

---

### Post by Nemooo on 2008-02-24
I've looked in the BIOS, but couldn't find anything, so I thought I'd try to install Windows again and then just move the files from the harddisk to a USB key and worry about the harddisk on Ubuntu later.

To my surprise Windows now can't find the harddisk either. I've tried installing Windows on the main harddisk before and that didn't affect the small one.

Any advise on how to rediscover the harddisk would be great.

---

### Post by jal_nl on 2008-02-25
> **Nemooo said:**
> I've looked in the BIOS, but couldn't find anything

What do you mean by this? Couldn't you find anything wrong, or couldn't you find any information related to harddisks? I'm pretty sure there should be at least some. If the BIOS also doesn't register the harddisk, it's probably dead.


JAL

---

### Post by Nemooo on 2008-02-25
To be honest I don't quite know, what to look for, but I tried enabling something, which looked like drives in the same menu as the big, working harddisk was in. When I rebooted the BIOS wrote it couldn't find those I had enabled, so I disabled them again. Should I try starting with them enabled, anyway?

How can a harddisk die?

---

### Post by Yellow Pasque on 2008-02-25
I don't think you've installed the disk properly. Can you feel it power up when you turn on the system?

If the older 40GB drive is a parallel ATA drive (PATA):
Are you sure you have the hard disk connected properly and don't have the ATA ribbon cable upside-down? Do you have a 4-pin Molex power plug from the power supply connected to the disk? Is the disk jumpered properly to Cable Select or Master.

If the 40GB drive is a serial ATA drive:
Do you have both SATA data cable (smaller plug) and SATA power cable (larger plug) plugged in? Does the drive also have a 4-pin Molex power conector? If so, did you connect both the Molex power and SATA power (if you did, you fried the drive).

---

### Post by Nemooo on 2008-02-25
I don't see why it shouldn't be plugged in properly as I never changed anything before I installed Ubuntu, but I'll see what I can do.

---

### Post by Yellow Pasque on 2008-02-25
Ok, I looked at the Dell manual. I'm guessing the 40GB drive is SATA, so make sure that SATA port is enabled in the BIOS. Also make sure that the SATA controller is not set to operate the drives in RAID mode.

---

### Post by jal_nl on 2008-02-27
> **Nemooo said:**
> To be honest I don't quite know, what to look for, but I tried enabling something, which looked like drives in the same menu as the big, working harddisk was in. When I rebooted the BIOS wrote it couldn't find those I had enabled, so I disabled them again. Should I try starting with them enabled, anyway?

Well, maybe there's someone in your surrounding that knows about BIOS and BIOS settings? Then he/she can take a look to see if there's anything wrong.

> How can a harddisk die?

Electronics failure/malfunction, most likely.


JAL

---

