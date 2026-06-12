---
title: "Harddrive Oddity!"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by wildone on 2007-06-20
hey guys, i got a strange problem i cant figure out. I have googled, i have asked guru's but with no avail.

WHAT I AM TRYING TO DO: Have VMware Machines have direct access to harddrives, eg i want to create a virtual harddrive in VMWare Server pointing to /dev/sda. 

WHAT IS MY PROBLEM: Harddrives change their oder "/dev/sda" at every boot (musical chairs!!). eg if i run "cat /proc/partitions" then reboot and run it again the hardrives just move around. This mean my VMs have a problem. 

WHAT I WOULD I LIKE TO HAPPEN: Hardrives stop changin their order at every boot. (no more musical chairs, if its /dev/sda, it stais like that forever)

WHAT I DO NOT WANT TO: Mount the drives in Ubuntu, we all know what can happen

MY CONFIG: Ubuntu 7.0.4, VMWare Server 1.0.3

APPENDIX

************************************************************************************
>lspci

00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
02:01.0 Ethernet controller: Intel Corporation 82547GI Gigabit Ethernet Controller
03:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:03.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
03:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
03:06.0 RAID bus controller: Silicon Image, Inc. Adaptec AAR-1210SA SATA HostRAID Controller (rev 02)
03:07.0 RAID bus controller: Adaptec Serial ATA II RAID 1420SA (rev 01)

************************************************************************************


************************************************************************************
>cat /proc/partitions

* this table changes every boot, SDA drive which is 250GB will become some other letter SD(ABCE..)

major minor  #blocks  name

   8     0  244140625 sda
   8     1  244131741 sda1
   8    16  244198584 sdb
   8    17  244196001 sdb1
   8    32  244198584 sdc
   8    33  244196001 sdc1
   8    48  390711384 sdd
   8    49  390708801 sdd1
   8    64   72613056 sde
   8    65          1 sde1
   8    66   10337796 sde2
   8    69   61761861 sde5
   8    70     505984 sde6
   8    80  244198584 sdf
   8    81  244196001 sdf1
   8    96  488386584 sdg
   8    97  488384001 sdg1
   8   112  488386584 sdh
   8   113  488384001 sdh1
   8   128  732574584 sdi
   8   129  732572001 sdi1
   8   144  244198584 sdj
   8   145  244196001 sdj1

************************************************************************************

---

### Post by wildone on 2007-06-20
does anyone know if CHS or LBA hdd mode hase anything to do with this?

---

### Post by ukripper on 2007-06-20
You need to assign correct UUID to each HDD in the fstab.

Can you post output of following command here:

```
ls -al /dev/disk/by-uuid
```

and also can you post content of your fstab

```
sudo gedit /etc/fstab
```

---

### Post by wildone on 2007-06-21
Thanks for that, i understand about fstab and i can mount the drives but i need VMware server to use the drives directry and it uses them via /dev/sda. But the drives just keep on moving around, see below:

i ran the [ls -al /dev/disk/by-uuid] then rebooted then [ls -al /dev/disk/by-uuid] agains here is the output:


lrwxrwxrwx 1 root root  10 2007-06-20 17:08 0840027F4002742A -> ../../sdb1
lrwxrwxrwx 1 root root  10 2007-06-20 17:08 2E84F48D84F45933 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2007-06-20 17:08 32ee675d-2c5d-4811-a9f0-2ee3d7adaccb -> ../../sda6
lrwxrwxrwx 1 root root  10 2007-06-20 17:08 443001D03001C9BE -> ../../sdd1
lrwxrwxrwx 1 root root  10 2007-06-20 17:08 4CF47FEBF47FD5A4 -> ../../sde1
lrwxrwxrwx 1 root root  10 2007-06-20 17:08 6C14A1F314A1C086 -> ../../sdg1
lrwxrwxrwx 1 root root  10 2007-06-20 17:08 7CD034E3D034A574 -> ../../sdj1
lrwxrwxrwx 1 root root  10 2007-06-20 17:08 AC1CD5DE1CD5A41C -> ../../sdi1
lrwxrwxrwx 1 root root  10 2007-06-20 17:08 DA440CE7440CC7E9 -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-06-20 17:08 e310c008-3a6b-46b9-9363-0b59b32f4168 -> ../../sdh1
lrwxrwxrwx 1 root root  10 2007-06-20 17:08 F840A4BF40A485CA -> ../../sdf1
lrwxrwxrwx 1 root root  10 2007-06-20 17:08 fb79e510-7e6c-4131-9096-8d8c737bde34 -> ../../sda2


**REBOOT


lrwxrwxrwx 1 root root  10 2007-06-21 00:29 0840027F4002742A -> ../../sdj1
lrwxrwxrwx 1 root root  10 2007-06-21 00:29 2E84F48D84F45933 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-06-21 00:29 32ee675d-2c5d-4811-a9f0-2ee3d7adaccb -> ../../sdi6
lrwxrwxrwx 1 root root  10 2007-06-21 00:29 443001D03001C9BE -> ../../sdb1
lrwxrwxrwx 1 root root  10 2007-06-21 00:29 4CF47FEBF47FD5A4 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2007-06-21 00:29 6C14A1F314A1C086 -> ../../sde1
lrwxrwxrwx 1 root root  10 2007-06-21 00:29 7CD034E3D034A574 -> ../../sdh1
lrwxrwxrwx 1 root root  10 2007-06-21 00:29 AC1CD5DE1CD5A41C -> ../../sdg1
lrwxrwxrwx 1 root root  10 2007-06-21 00:29 DA440CE7440CC7E9 -> ../../sdi5
lrwxrwxrwx 1 root root  10 2007-06-21 00:29 e310c008-3a6b-46b9-9363-0b59b32f4168 -> ../../sdf1
lrwxrwxrwx 1 root root  10 2007-06-21 00:29 F840A4BF40A485CA -> ../../sdd1
lrwxrwxrwx 1 root root  10 2007-06-21 00:29 fb79e510-7e6c-4131-9096-8d8c737bde34 -> ../../sdi2

---

### Post by wildone on 2007-06-24
i am going to try udev rules, see if that will work. any one know how to write them?

---

### Post by ukripper on 2007-06-24
You can only have 4 primary partitions even under VM. How many you have?

---

### Post by wildone on 2007-06-24
> **ukripper said:**
> You can only have 4 primary partitions even under VM. How many you have?

I have 8 linked to a VISTA VM, 6 of those are marked as primary works like a charm. I fixed my problem using udev rules. Its all working now :D :popcorn:

---

### Post by ukripper on 2007-06-25
> **wildone said:**
> I have 8 linked to a VISTA VM, 6 of those are marked as primary works like a charm. I fixed my problem using udev rules. Its all working now :D :popcorn:

just curious what exactly went wrong? And how did you  resolve it?

---

### Post by wildone on 2007-06-25
> **ukripper said:**
> just curious what exactly went wrong? And how did you  resolve it?

Well all the drives i have are SATA and for some reason kernel loads all of them in different order at boot into /sys/block and names them sda, sdb ...


I created  a file "70-local.rules" purpously after "65-persistent-storage.rules", for a reason that i let the udev create all the symlink everywhere it want to and then just rename the disk and partitions to the names i want.
see "70-local.rules" file for more detail.

I used the disk serial to be exact i am picking the right disk, unlike some examples online!

To find out your disk serial do:  

	#-n = name

	*udevinfo -q all -n /dev/sda *  

	OR	

	#-p = path

	*udevinfo -q all -p /sys/block/sda*


********************* udevinfo -q all -n /dev/sda

P: /block/sdi   **<- path is still what KERNEL load it as **
N: sda		**<- but the name is what i gave it.**
L: 0
S: disk/by-id/scsi-1ATA_WDC_WD740GD-00FLA0_WD-WMAKE1145287
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_VENDOR=ATA
E: ID_MODEL=WDC_WD740GD-00FL
E: ID_REVISION=21.0
E: ID_SERIAL=1ATA_WDC_WD740GD-00FLA0_WD-WMAKE1145287
E: ID_SERIAL_SHORT=ATA_WDC_WD740GD-00FLA0_WD-WMAKE1145287
E: ID_TYPE=disk
E: ID_BUS=scsi
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0




********************* 70-local.rules

#-> for disks these rules will apply
#
#KERNEL=="sd*[!0-9]" means match drive named {sd[!=not 0-9]} only sda...sdz 	 
#NAME="sda" set the name to SDA etc
#
#-> for partitions these rules will apply
#
#KERNEL=="sd*[0-9]" now match all other sda0..9 etc 				 
#NAME="sda%n" %n will be the partition number
#
#


#D OS & ServerData
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD740GD-00FLA0_WD-WMAKE1145287", NAME="sda"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD740GD-00FLA0_WD-WMAKE1145287", NAME="sda%n"

#E Data1
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD2500JD-75FYB0_WD-WMAEH1924391", NAME="sdb"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD2500JD-75FYB0_WD-WMAEH1924391", NAME="sdb%n"

#F Data2 - VM Store
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD2500JD-00GBB0_WD-WMAEP1708011", NAME="sdc"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD2500JD-00GBB0_WD-WMAEP1708011", NAME="sdc%n"

#G Data3
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD2500JD-50FYB0_WD-WMAEH2709188", NAME="sdd"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD2500JD-50FYB0_WD-WMAEH2709188", NAME="sdd%n"

#H Data4
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD2500JD-50FYB0_WD-WMAEH2708798", NAME="sde"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD2500JD-50FYB0_WD-WMAEH2708798", NAME="sde%n"

#I Data5
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD2500JD-40GBB2_WD-WMAEP3646983", NAME="sdf"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD2500JD-40GBB2_WD-WMAEP3646983", NAME="sdf%n"

#J Data6
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD4000YR-01PLB0_WD-WMAMY1186058", NAME="sdg"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD4000YR-01PLB0_WD-WMAMY1186058", NAME="sdg%n"

#K Data7
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_ST3750640AS_5QD0426Q", NAME="sdh"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_ST3750640AS_5QD0426Q", NAME="sdh%n"

#L Data8
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD5000AAKS-00TMA0_WD-WCAPW0740007", NAME="sdi"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD5000AAKS-00TMA0_WD-WCAPW0740007", NAME="sdi%n"

#M Data9
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD5000AAKS-00TMA0_WD-WCAPW0736066", NAME="sdj"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_WDC_WD5000AAKS-00TMA0_WD-WCAPW0736066", NAME="sdj%n"

---

### Post by ukripper on 2007-06-25
Great job mate. It could be a good HowTo

---

### Post by wildone on 2007-06-26
> **ukripper said:**
> Great job mate. It could be a good HowTo

I can write a more detailed one, i had a long play with it there are lots and lots of things you can do with it, just point me in the right direction.
does any one want me to write a UDEV rules HOWTO/FAQ?

---

