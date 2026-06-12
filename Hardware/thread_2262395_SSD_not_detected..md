---
title: "SSD not detected."
date: 2015-01-24
forum: Hardware
---

### Post by josh112 on 2015-01-24
Hi I'm new to Ubuntu (yesterday new). I installed Ubuntu 14.10LTS  on my Lenovo yoga 2 11 and was able to get some things working like wifi and brightness but I have a slight problem that has been bugging me. I installed Ubuntu on my HDD but I can't seem to access my SSD; I can't see my SSD in my left window pane or in "disks". I'd like to have my SSD auto-mount every time I boot my laptop; btw my SSD only contains data - no other OS. Please help (and thanks for reading).

---

### Post by oldfred on 2015-01-24
Does BIOS show SSD correctly?
Post this:
sudo parted -l
sudo fdisk -lu

---

### Post by mooreted on 2015-01-24
Open a terminal and give use the output of the following command:

sudo fdisk -l

(That's a lower-case L)

---

### Post by josh112 on 2015-01-24
sudo parted -l :

```
josh@josh-Lenovo-Yoga-2-11:~$ sudo parted -l
[sudo] password for josh: 
Model: ATA WDC WD5000MPCK-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End    Size    File system     Name  Flags
 1      1049kB  538MB  537MB   fat32                 boot
 2      538MB   496GB  495GB   ext4
 3      496GB   500GB  4172MB  linux-swap(v1)
```

sudo fdisk -lu:

```
josh@josh-Lenovo-Yoga-2-11:~$ sudo fdisk -lu
[sudo] password for josh: 


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x219c8c9c


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.
josh@josh-Lenovo-Yoga-2-11:~$ 
```

sudo fdisk -l:

```
josh@josh-Lenovo-Yoga-2-11:~$ sudo fdisk -l


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x219c8c9c


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.
josh@josh-Lenovo-Yoga-2-11:~$ 
```


Sorry it took me a long time to reply, I was out.

---

### Post by oldfred on 2015-01-25
It only shows the 500GB drive. I assume that is not the SSD?

Does BIOS show drive?
Or is SSD an external drive?

---

### Post by josh112 on 2015-01-25
I'm not sure where to find the SSD in BIOS. It's not an external SSD drive either. When I was running Ubuntu from my usb (created with lili usb creator) It showed my SSD on the left pane, but when I installed Ubuntu it did not show. I thought it was a 25gb SSD but from the manufacturer site it shows 16gb: [http://shop.lenovo.com/ca/en/laptops/lenovo/yoga-laptop-series/yoga-2-11/#techspecs](http://shop.lenovo.com/ca/en/laptops/lenovo/yoga-laptop-series/yoga-2-11/#techspecs)

In BIOS it seems to be using AHCI for drives, is that good or bad? What else could I try?

---

### Post by oldfred on 2015-01-25
AHCI is required for SSD, for trim to work.

Is this a new M.2 type SSD that is plugged/soldered directly into motherboard?
But it should still be shown in BIOS. It should show all hard drives by model.

The small SSD are used by vendors to meet the Windows requirement of quicker booting. That is now why Windows uses fast boot or always on hibernation. And then the hibernation file is on the SSD. That often is Intel SRT or similar Intel based configuration.

        Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)
For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 
For MBR systems, you need a partition type of 0x84[2].
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

