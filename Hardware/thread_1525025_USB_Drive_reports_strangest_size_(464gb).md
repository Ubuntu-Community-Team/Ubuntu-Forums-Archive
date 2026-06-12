---
title: "USB Drive reports strangest size (4/64gb)"
date: 2010-07-06
forum: Hardware
---

### Post by maweki on 2010-07-06
Hey,

I have a new usb stick here which I planed to replace an old failing server harddrive with.

The drive is 4gb in size (that's what is printed on the packaging) but this is the fdisk output:

```
Disk /dev/sdb: 68.7 GB, 68718428160 bytes
240 heads, 63 sectors/track, 8876 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x020e4436

  Device Boot      Start        End      Blocks  Id  System
/dev/sdb1  *          1        515    3888096+  b  W95 FAT32 
```

As you can see, the factory default Fat32 partition is in place but the drive is reported as 64GB. Now I do not really know how to format the drive (or how much really is usable). The Server has a HDD of the capacity of 10gb (whis is only used 20%) so I allready have to resize partitions and stuff and it would be useful to know, what to do about the wrong capacity (or is it actually a 64gb drive?)

---

### Post by maweki on 2010-07-06
After some IRC-Help I dded the partition table an generated a new one. Same output:

```
# root@PartedMagic:~# fdisk -l /dev/sdb
#  
# Disk /dev/sdb: 68.7 GB, 68718428160 bytes
# 255 heads, 63 sectors/track, 8354 cylinders
# Units = cylinders of 16065 * 512 = 8225280 bytes
# Sector size (logical/physical): 512 bytes / 512 bytes
# I/O size (minimum/optimal): 512 bytes / 512 bytes
# Disk identifier: 0x00000000
#  
# Disk /dev/sdb doesn't contain a valid partition table 
```

here before generating the new table with gparted.

---

### Post by jquis8411 on 2010-07-07
I saw your problem while looking for answers to my owm but maybe I can help. Im just learning ubuntu but on my windows machine I use a great little program called H2testw. its a free down load. All it does is write to a drive till capacity then reads it back to verify that the info isnt corrupted but its great to verify the actual size of a disk or stick regardless of whats printed on the package or what ever unscrupulous person reprogrammed it to read as larger .

---

