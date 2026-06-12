---
title: "Using Intel Optane on Win 10 / Ubuntu dual boot"
date: 2019-12-17
forum: Hardware
---

### Post by bitow on 2019-12-17
I’m trying to use an Optane Memory in my dual boot system, but I’ve been getting this “problem loading uefi db x.509 certificate (-65)” error on every boot. Secure boot already disabled and for some reason Legacy isn’t available.
I know that Optane is not supported on Linux but I really need it on Windows, and unfortunatly I still need Windows. Does anyone know how to fix this?

---

### Post by oldfred on 2019-12-17
What optane do you have? Many were used just for Windows fast startup which is boot hibernation.
And then only used the amount of RAM. Some with a 32GB SSD and 8GB RAM used remaining 24GB as / (root) for Ubuntu with /home on HDD. Then Ubuntu entire system, not just boot is faster.

       Optane Memory Module - Frequently Asked Questions 
[https://www.dell.com/support/article/us/en/04/sln306745/optane-memory-module-frequently-asked-questions?lang=en](https://www.dell.com/support/article/us/en/04/sln306745/optane-memory-module-frequently-asked-questions?lang=en)
Optane enabled system may not boot when a Hard Drive or Optane device fails 
[https://www.dell.com/support/article/us/en/04/sln306541/optane-enabled-system-may-not-boot-when-a-hard-drive-or-optane-device-fails?lang=en](https://www.dell.com/support/article/us/en/04/sln306541/optane-enabled-system-may-not-boot-when-a-hard-drive-or-optane-device-fails?lang=en)
AHCI vs RAID speed same, one user says power use lower with RAID?
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)

---

### Post by bitow on 2019-12-18
Oh yes, I failed to mention that the system boots with the error fine so far, but a couple of days ago I was getting kernel panic and had to format the Ubuntu partition. As you mentioned I just use Optane for faster boots on Windows (got it as a bonus when I bought the notebook), it has 16GB and is used on a 1TB HDD (150GB for Ubuntu and the rest for Windows). The computer doesn't have SSD, so I rely on the Optane.
If I understood the concept of the Optane correctly it is boosting the physical drive as a whole, therefore trying to boost the Ubuntu partition and failing, generating that error I mentioned. Am I doing anything wrong with the partitions here?

Edit: No errors when Optane is disabled.

---

### Post by oldfred on 2019-12-18
I do not know if Optane is just a boot cache or a full hard drive cache. It probably is a small SSD. On some systems it then is seen as a second drive.
Post these:
sudo fdisk -lu
sudo parted -l
       sudo lshw -C Disk -short

---

### Post by bitow on 2019-12-18
Here you go.

sudo lshw -C Disk -short :

```

H/W path       Device     Class          Description
====================================================
/0/1/0.0.0     /dev/sda   disk           1TB WDC WD10SPZX-21Z

```

sudo parted -l :

```

Warning: Not all of the space available to /dev/sda appears to be used, you can
fix the GPT to use all of the space (an extra 4521 blocks) or continue with the
current setting? 
Fix/Ignore? ignore                                                        
Model: ATA WDC WD10SPZX-21Z (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  106MB   105MB   fat32        EFI system partition          boot, esp
 2      106MB   123MB   16,8MB               Microsoft reserved partition  msftres
 3      123MB   886GB   886GB   ntfs         Basic data partition          msftdata
 4      886GB   999GB   113GB   ext4
 5      999GB   1000GB  1072MB  ntfs         Basic data partition          hidden, diag

```

sudo fdisk -lu :

```

Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: A9FDE153-5098-4072-9707-4ED3476F220D

Device          Start        End    Sectors    Size Type
/dev/sda1        2048     206847     204800    100M EFI System
/dev/sda2      206848     239615      32768     16M Microsoft reserved
/dev/sda3      239616 1729780100 1729540485  824,7G Microsoft basic data
/dev/sda4  1729781760 1951426559  221644800  105,7G Linux filesystem
/dev/sda5  1951426560 1953520590    2094031 1022,5M Windows recovery environment

```

---

### Post by oldfred on 2019-12-18
Please do not post screenshots of terminal output.
Better to just copy & paste & then if longer (more than a couple of lines) use code tags to preserve formatting & make it easier to read.
       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[http://www.bbcode.org/reference.php](http://www.bbcode.org/reference.php)
If using Quick Reply then ```
 at the beginning and 
``` at the end. 
( [noparse]```
 and 
```[/noparse] ) 

You only show one drive.
You do not need to show all the loop devices which are from the install of snaps.

---

### Post by bitow on 2019-12-18
I'm very sorry, I'll edit the previous reply with the correct formatting.

---

### Post by oldfred on 2019-12-18
Thanks for updating.

Not sure if then changing settings in UEFI on drive, may then show optane separately or not.

---

