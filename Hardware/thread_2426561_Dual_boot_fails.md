---
title: "Dual boot fails"
date: 2019-09-10
forum: Hardware
---

### Post by satimis on 2019-09-10
Configuration - Dual boot
SSD 250G - Ubuntu 16.04
SSD 1TB -Ubuntu 16.04
WD 1TB - for storage
WD 2TB - for storage

After changing SSD 1TB to a new SSD 2TB - Ubuntu 16.04, dual boot failed.  It always boots SSD 2TB even selecting to boot SSD 250G.

To boot SSD 250G I have to unplug the cables of SSD 2TB.

Please advise how to check and to sort out this problem.

Thanks in advance

Regards
satimis

---

### Post by oldfred on 2019-09-10
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by satimis on 2019-09-11
> **oldfred said:**
> May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Thanks for your advice.

I'll follow the 2nd option: install Boot-Repair in Ubuntu
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```

Do I need to disconnect both SSDs ?  I have important data on SSD 2TB and the storage WD disks.

Thanks

Regards
satimis

---

### Post by yancek on 2019-09-11
> Do I need to disconnect both SSDs ?

You need to download and run the boot repair software as instructed and select the Create BootInfo Summary option.  Do NOT try to make any repairs.  You will need both drives attached to get accurate and complete information.  The software gathers information only and will give you a link to post here when finished.  No changes will be made unless you tell it to so make sure you ONLY run the Create BootINfo Summary option.

---

### Post by satimis on 2019-09-11
> **yancek said:**
> You need to download and run the boot repair software as instructed and select the Create BootInfo Summary option.  Do NOT try to make any repairs.  You will need both drives attached to get accurate and complete information.  The software gathers information only and will give you a link to post here when finished.  No changes will be made unless you tell it to so make sure you ONLY run the Create BootINfo Summary option.
Hi,

Thanks for your advice,

I'll run an USB booting the desktop PC and install Boot-Repair on the USB terminal.

If I understand your advice correctly.  After starting the Boot-Repair software selecting "Create BootInfo Summary option" and continue ?

Are following video relevant to my case?
1)
Repair Ubuntu with Boot-Repair
[https://www.youtube.com/watch?v=BeNtnpwoxN4](https://www.youtube.com/watch?v=BeNtnpwoxN4)

2)
How to boot repair Linux grub
[https://www.youtube.com/watch?v=FiJokVR9YaY](https://www.youtube.com/watch?v=FiJokVR9YaY)
select --> creating_a_Booinfo summary
Then continue ?

Please see attached Screenshot

Thanks

Regards
satimis

---

### Post by oldfred on 2019-09-11
I am not a fan of videos as you cannot copy & paste. They often go by too fast to use to actually do what they show. 
But the video gives you an idea of what you will see.

Your attached screen shot is part of first link to how to install Boot-Repair & its screenshot.

---

### Post by satimis on 2019-09-13
> **oldfred said:**
> I am not a fan of videos as you cannot copy & paste. They often go by too fast to use to actually do what they show. 
But the video gives you an idea of what you will see.

Your attached screen shot is part of first link to how to install Boot-Repair & its screenshot.
Hi,

Thanks for your advice.  I have new discovery as follow.

Now I have 2 SSD disks connected and boot SSD1(2TB).  It seems to me that SSD2(240G) is not mounted automatically at boot.  Nor I can find it on the left vertical menu bar.

On terminal:
&#10219; sudo fdisk -l > diskdata.txt

&#10219; cat diskdata.txt```

Disk /dev/loop0: 88.7 MiB, 92983296 bytes, 181608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.7 MiB, 90906624 bytes, 177552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 202.9 MiB, 212713472 bytes, 415456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 89 MiB, 93327360 bytes, 182280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x429ca318

Device     Boot   Start        End    Sectors  Size Id Type
/dev/sda1  *       2048    1499135    1497088  731M 83 Linux
/dev/sda2       1501182 3907028991 3905527810  1.8T  5 Extended
/dev/sda5       1501184 3907028991 3905527808  1.8T 8e Linux LVM


Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x1e66a37e

Device     Boot   Start       End   Sectors   Size Id Type

/dev/sdb1  *       2048    999423    997376   487M 83 Linux
/dev/sdb2       1001470 488396799 487395330 232.4G  5 Extended
/dev/sdb5       1001472 488396799 487395328 232.4G 8e Linux LVM


Disk /dev/sdc: 1.4 TiB, 1500301910016 bytes, 2930277168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x09ab06ac

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdd1        2048 3907029167 3907027120  1.8T 83 Linux


Disk /dev/mapper/ubuntu--vg-root: 1.8 TiB, 1998602633216 bytes, 3903520768 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-swap_1: 976 MiB, 1023410176 bytes, 1998848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

Any advice?  Thanks in advance.

Regards
satimis

---

### Post by oldfred on 2019-09-13
Many SSD particularly NVMe drives have needed firmware updates, even if new, to work in Linux.
Have you checked to see if you have latest firmware in your SSDs.
You  probably should also make sure UEFI is the most current version available.

---

### Post by satimis on 2019-09-13
> **oldfred said:**
> Many SSD particularly NVMe drives have needed firmware updates, even if new, to work in Linux.
Have you checked to see if you have latest firmware in your SSDs.
You  probably should also make sure UEFI is the most current version available.

How to check firmware in SSDs ?

I don't think the SSD in question is a NVMe drive.

&#10219; lsscsi```

[0:0:0:0]    disk    ATA      Samsung SSD 860  1B6Q  /dev/sda 
[1:0:0:0]    cd/dvd  SONY     DVD RW AW-G170S  1.72  /dev/sr0 
[2:0:0:0]    disk    ATA      SanDisk SDSSDH32 10RL  /dev/sdb 
[3:0:0:0]    disk    ATA      WDC WD1502FAEX-0 1D05  /dev/sdc 
[4:0:0:0]    disk    ATA      WDC WD2005VBYZ-0 RR07  /dev/sdd 

```

&#10219; sudo hdparm -I /dev/sdb > SanDisk.txt
&#10219; cat SanDisk.txt```

/dev/sdb:

ATA device, with non-removable media
	Model Number:       SanDisk SDSSDH3250G                     
	Serial Number:      173058421625        
	Firmware Revision:  X61110RL
	Media Serial Num:   
	Media Manufacturer: 
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
	Used: unknown (minor revision code 0x005e) 
	Supported: 11 10 9 8 7 6 5 
	Likely used: 11
Configuration:
	Logical		max	current
	cylinders	16383	0
	heads		16	0
	sectors/track	63	0
	--
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  488397168
	Logical  Sector size:                   512 bytes
	Physical Sector size:                   512 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:      238475 MBytes
	device size with M = 1000*1000:      250059 MBytes (250 GB)
	cache/buffer size  = unknown
	Form Factor: 2.5 inch
	Nominal Media Rotation Rate: Solid State Device
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 1	Current = 1
	Advanced power management level: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	   *	48-bit Address feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	    	unknown 119[8]
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Gen3 signaling speed (6.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Phy event counters
	   *	READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
	   *	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	    	Asynchronous notification (eg. media change)
	   *	Software settings preservation
	    	Device Sleep (DEVSLP)
	   *	DOWNLOAD MICROCODE DMA command
	   *	WRITE BUFFER DMA command
	   *	READ BUFFER DMA command
	   *	Data Set Management TRIM supported (limit 8 blocks)
	   *	Deterministic read ZEROs after TRIM
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	2min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 5001b444a992b3d3
	NAA		: 5
	IEEE OUI	: 001b44
	Unique ID	: 4a992b3d3
Device Sleep:
	DEVSLP Exit Timeout (DETO): 30 ms (drive)
	Minimum DEVSLP Assertion Time (MDAT): 30 ms (drive)
Checksum: correct

```

I think I'll perform Boot-Repair after having copied the important data from both SSDs first.


Edit
===
The firmware version of SSD1 (2TB)
&#10219; sudo smartctl --xall /dev/sda | grep -i firmware```

Firmware Version: RVT01B6Q

```

The firmware version of SSD2 (250G)

&#10219; sudo smartctl --xall /dev/sdb | grep -i firmware```

Firmware Version: X61110RL

```

But I have no idea whether they are uptoday?

Regards
satimis

---

### Post by oldfred on 2019-09-13
Google tells me that Sandisk has Dashboard that includes updates. Probably only for Windows.

[https://kb.sandisk.com/app/answers/detail/a_id/15108/~/sandisk-ssd-dashboard-support-information](https://kb.sandisk.com/app/answers/detail/a_id/15108/~/sandisk-ssd-dashboard-support-information)

Samsung has magician, but Linux version was buried away in its commercial support area and never worked right for my older 840.
Again Windows versions.[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)

---

### Post by satimis on 2019-09-21
> **oldfred said:**
> Google tells me that Sandisk has Dashboard that includes updates. Probably only for Windows.

[https://kb.sandisk.com/app/answers/detail/a_id/15108/~/sandisk-ssd-dashboard-support-information](https://kb.sandisk.com/app/answers/detail/a_id/15108/~/sandisk-ssd-dashboard-support-information)

Samsung has magician, but Linux version was buried away in its commercial support area and never worked right for my older 840.
Again Windows versions.[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
Hi,

Thanks for your advice.

While copying the important data from the 2TB-SSD to the storage WD hard-drive I read the document in re replacing the old 1TB-SSD with the new 2TB-SSD

Previous configuration```

Dual boot
1TB-SSD Ubuntu 16.04
250G-SSD Ubuntu 16.04

Storage Disk:
1.5TB WD Hard drive
2TB WD Hard drive

```

Present configuration```

2TB-SSD Ubuntu 16.04
250G-SSD Ubuntu 16.04

Storage Disk:
1.5TB WD Hard drive
2TB WD Hard drive

```

Steps performed to replace the old 1TB-SSD
1. removed all disks with only the new 2TB-SSD connected.
2. installed Ubuntu 16.04 from an USB stick to the new 2TB-SSD
3. reconnected the old 1TB-SSD and storage WD hard drives to PC
4. copied all data from 1TB-SSD to the new 2TB-SSD
5. removed the 1TB-SSD
6. reconnected 250G-SSD to PC

It came to present situation unable booting 250G-SSD unless disconnecting the 2TB-SSD.  The storage WD drives are automatically mounted on booting and can be found on the left vertical menu bar.

I suppose the 250G-SSD also mounted automatically on booting which can be found running "sudo fdisk -l" on terminal.  But it can't be found on the left vertical menu bar

Any advice.  Thanks

Regards
satimis

---

### Post by oldfred on 2019-09-21
Did you ever post link to summary report from Boot-Repair?
That shows lots of details on configuration. 
May have conflict like duplicate UUIDs or something which report will show.
Run from Live installer.

If you do not post within next few hours, I probably will not see it for a couple of weeks. But others may review report and see something.

---

### Post by satimis on 2019-09-21
> **oldfred said:**
> Did you ever post link to summary report from Boot-Repair?
That shows lots of details on configuration. 
May have conflict like duplicate UUIDs or something which report will show.
Run from Live installer.

- snip -

Sorry no.  Because I have lot of important data to be removed from the 2TB-SSD to the storage drives.

satimis

---

### Post by satimis on 2019-09-22
Hi all,

boot summary;
[http://paste.ubuntu.com/p/FZPxDB2Hns/](http://paste.ubuntu.com/p/FZPxDB2Hns/)

USB drive - OS Ubuntu 18.04

Drives connection:-
250G SSD
2TB SSD
1.5TB WD hard drive - storage

2TB WD hard drive (storage) is not connected because important data on this drive.

Thanks

Regards
satimis

---

### Post by satimis on 2019-09-25
Hi all,

New discovery:

I have a spare PC, multiple booting with following configuration:
CPU AMD 8-cores
RAM 8G
1TB-SSD(Ubuntu 16.04)
128G-SSD(Ubuntu 18.04)
128G-SSD(Ubuntu 16.04)

They work without problem.  I can boot any SSD disk.

Performed following test:
Daily working PC, dual boot
CPU AMD 8-cores
RAM 32G
2TB-SSD(Ubuntu 16.04)
250G-SSD(Ubuntu 16.04)

1) Replaced the 250GB-SSD disk with the 128G-SSD Ubuntu(16.04) disk from the spare PC.
2) Same problem was found.  I couldn't boot it if the 2TB-SSD disk connected.  But with 2TB-SSD disk disconnected I can boot 128G-SSD(Ubuntu 16.04) without problem.

I suppose the problem was caused because when I installed the OS of the 2TB-SSD disk I have the 250G-SSD disk disconnected from the PC.

I think the solution may-be to reinstall the OS of the 250G-SSD with the 2TB-SSD(Ubuntu 16.04) connected to the working PC during installation.  I'm considering to purchase a new 500G-SSD disk to perform this test.  The 250G-SSD(Ubuntu 16.04) disk will be moved to the spare PC.

Any comment would be appreciated?  Thanks in advance.

Regards
satimis

---

