---
title: "Problems adding disk to degraded RAID5 after upgrade"
date: 2011-05-21
forum: Hardware
---

### Post by sds50 on 2011-05-21
On upgrading to Natty (11.04), my RAID5 array seems to have degraded itself:

```

$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd[3] sdc[2] sdb[1]
      2930287488 blocks level 5, 64k chunk, algorithm 2 [4/3] [_UUU]
      
unused devices: <none>
```

This array has previously been working fine for over a year over various different linux installs. I have tried a few things to get it back in order - none of which seem to be working.

Trying the obvious, of just adding the drive back in:

```

$ sudo mdadm /dev/md0 -a /dev/sda 
mdadm: Cannot open /dev/sda: Device or resource busy
```

This confused me somewhat. Booting from a livecd and building the array manually with "mdadm --assemble --scan -v" tells me that mdadm doesn't find a RAID superblock on /dev/sda which is a little weird.

Attempting to add the drive again as before [but from the liveCD], mdadm tells me that the drive is not of the correct size to be added to the array. Now alarm bells are ringing a little!

All 4 disks are the same model:

```

$ sudo hdparm -I /dev/sd{a,b,c,d} | grep Model
	Model Number:       SAMSUNG HD103SJ                         
	Model Number:       SAMSUNG HD103SJ                         
	Model Number:       SAMSUNG HD103SJ                         
	Model Number:       SAMSUNG HD103SJ 
```

Concerningly, looking at the number of addressable sectors:

```

$ sudo hdparm -I /dev/sd{a,b,c,d} | grep "\(LBA48\)"
	LBA48  user addressable sectors: 1953523055
	LBA48  user addressable sectors: 1953525168
	LBA48  user addressable sectors: 1953525168
	LBA48  user addressable sectors: 1953525168

$ sudo hdparm -I /dev/sd{a,b,c,d} | grep "\(M = 1024\)"
	device size with M = 1024*1024:      953868 MBytes
	device size with M = 1024*1024:      953869 MBytes
	device size with M = 1024*1024:      953869 MBytes
	device size with M = 1024*1024:      953869 MBytes
```

Showing that /dev/sda has fewer available sectors than the others, and is smaller. fdisk agrees, althegh the number of LBA user addressable sectors, and CHS current addressable sectors is the same across the drives.

This leaves me really rather boffled. Sadly I hadn't checked the RAID state immediately before reinstalling (I should have), so I can't be sure if this is hardware, software or other oddities going on. It had, however, been working correctly for over a year across various installs.

Does anyone have any ideas for what I should look at/what is likely to be going on?

---

### Post by sds50 on 2011-05-21
Further to this, using a Maverick (10.10) livecd the disks all register the correct size and can be added to the array correctly. Currently the array is being rebuilt.

We shall see if this survives a boot back into 11.04 - I have my doubts :-S.

---------------
Edit:
Sadly my intuition is correct. Despite rebuilding correctly under 10.10, it falls apart as soon as I boot into 11.04. However I have eliminated the "Device or Resource Busy" error by blacklisting /dev/sda in lvm.conf

--> The only problem now seems to be that the drive is reporting a different size to the other 3 identical drives. It presumably doesn't do this under 10.10, or it wouldn't work nicely. Not sure what to do about this.

---

