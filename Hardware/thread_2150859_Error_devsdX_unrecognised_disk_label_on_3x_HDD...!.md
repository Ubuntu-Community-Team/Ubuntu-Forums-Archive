---
title: "Error: /dev/sdX: unrecognised disk label on 3x HDD...!"
date: 2013-06-02
forum: Hardware
---

### Post by sauvagii on 2013-06-02
Hi all, 

A few days ago I decided to do a bit of hardware upgrading on an ageing linux machine I keep in my loft basically as a central NAS for movies, backups etc. 

Until now this ran an old distro of Fedora (14), on a (very old) dual processor Xeon board.  Installed in the machine were a mix of HDDs of various sizes and formats.  

I shut it down and took the machine apart to install a new CPU,board etc, with the plan to install a new version Ubuntu to replace it. 

I'm able to access and mount two other drives, one was ext3 and one was NTFS formatted. 

There are 3 HDDS that were ext3 format that now I cannot get access to at all.  They were working immediately prior to the final shutdown of the old setup.  Googled for hours on end and not been able to get any solution. 

Currently running PartedMagic from USB to see if I can work out why.   Have run all the SMART checks etc, and all disks reporting as normal/healthy.

Used parted/gparted with no luck and fdisk gives get this output (with the other working stuff removed):

```
[COLOR=#000000][FONT=Verdana]root@partedmagic:~# fdisk -l[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]*(other functioning drive data removed here)*[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Error: /dev/sdb: unrecognised disk label
Model: ATA WDC WD5000AAKS-0 (scsi)                                        
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: /dev/sdc: unrecognised disk label
Model: ATA WDC WD5000AAKS-0 (scsi)                                        
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: /dev/sdd: unrecognised disk label
Model: ATA SAMSUNG HD103SJ (scsi)                                         
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:[/FONT][/COLOR]

```

Does anyone have any suggestions what to do next?

---

### Post by ahallubuntu on 2013-06-02
~

---

### Post by sauvagii on 2013-06-02
Hey there, and thanks for the quick response. 

I've tried that - with each individual drive, and the same result.  Also tried all the drives on a PCI RAID card that I've installed (though currently nothing connected to it). 

Have also verified that existing, readable disks work on the other sata ports.  (spent most of my weekend unplugging, replugging and rebooting!)

---

### Post by ahallubuntu on 2013-06-02
Silly question: have you verified the power connections on these other drives?  Tried a different power supply?  Tried different SATA cables?

---

### Post by sauvagii on 2013-06-02
Yeah, and also tried each of them in an external eSata dock to the same result :(

---

### Post by ahallubuntu on 2013-06-02
~

---

### Post by sauvagii on 2013-06-02
Tried connecting them to a Win machine, and all the partitions show as Unallocated.  A partition recovery tool showed one of the working drives as EXT3, and that one's fine. 

No encryption, but am normally pretty careful with machines when working on them incase of ESD... but 3 HDDs in one go?!  That's got to be the worst luck ever! 

Gutting! :(

---

### Post by ahallubuntu on 2013-06-02
~

---

### Post by sauvagii on 2013-06-02
Have tried ext2fs and Diskinternals, no luck with either.  All the disks are internal drives - just tried in the eSata dock to see if there was any difference.

---

