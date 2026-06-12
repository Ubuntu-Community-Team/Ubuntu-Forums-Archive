---
title: "Dual boot with Windows XP installed"
date: 2008-04-24
forum: Hardware
---

### Post by Dano1970 on 2008-04-24
Hello All,
I have a Dell Precision M6300 that currently has the factory installed restore partition intact (~86 Mb FAT). It also came with the rest of the HDD formatted as one drive (NTFS C:) with Windows XP Pro currently living on it. I have since used Partition Magic 8.0 to free up 40 GB on the back end of the drive. Currently Windows sees that extra disk space as unallocated and not formatted with any specific file system (NTFS, FAT, etc).
My problem is that when I boot to the Ubuntu provided media for 5.04, the install crashes at the partition check. I receive "No partitionable media were found. Please check that a hard disk is attached to this machine."
I have also tried to boot to the live CD also with no success.
Any ideas?

Thanks for any help,
Dano

---

### Post by Dano1970 on 2008-04-24
Update:
I have now just performed the article "Using QtParted from the System Rescue CD" and have actually created a swap file partition, a root partition, and what will eventually be a home partition. 
The ubuntu install still cannot see any partitionable media...??
My thoughts are hearkening back to possibly having to add an entry for linux into the windows boot.ini file, can anyone confirm this?
Thanks,
Dano

---

### Post by Dano1970 on 2008-04-24
Update: Just finished downloading and burning the 8.04 and thus so far so good.
Thanks,
Dano

---

