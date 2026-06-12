---
title: "Partitioning problem. Need help."
date: 2008-10-24
forum: General Help
---

### Post by shamusl on 2008-10-24
I have a windows partition (sda1 - boot device - NTFS), and want to get rid of it completely and expand my /home partition. I've seen some guides but they aren't too decisive. My /home partition is sda2 (EXT3 - 107 GB), / is sda4 (EXT3 - 15 GB). I want to make sda4 (/) my boot device, as well as eliminate the startup (GRUB splash screen) Anybody got any ideas?

---

### Post by zvacet on 2008-10-24
You can use [Gparted live Cd]("http://gparted.sourceforge.net/") to delete Windows partition and on that unallocated space expand your home partition.

---

### Post by shamusl on 2008-10-24
> **zvacet said:**
> You can use [Gparted live Cd]("http://gparted.sourceforge.net/") to delete Windows partition and on that unallocated space expand your home partition.

If I delete the windows partition (which is boot), wouldn't my system not be able to start?

---

### Post by zvacet on 2008-10-25
> If I delete the windows partition (which is boot), wouldn't my system not be able to start?

In that case you will [reinstall grub.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by vanadium on 2008-10-25
If you want to expand your home directory, you indeed will need to reinstall grub in order to make your system bootable again. It would involve deleting your sda1, moving your sda2 to the front (very lengthy process, not guaranteed to be successfull) and enlarging it to fill the free space. Because a partition is removed, the device assignations would change, hence grub needs to be adjusted.

Depending on your level of experience, reformatting your sda1 to ext3 and then using that as additional storage space would be a far easier solution.

---

### Post by caljohnsmith on 2008-10-25
[quote=shamusl]If I delete the windows partition (which is boot), wouldn't my system not be able to start?[/quote]
One thing you should be aware of is that your Windows partition is probably marked as the "active" partition, and that there are some BIOSes that will refuse to boot a drive that doesn't have one partition marked as active; therefore if you delete your Windows partition, I would recommend setting one of your other partitions as the active partition to make sure your BIOS doesn't choke. To see which partition is marked active, you can do:
```
sudo fdisk -l
```
And the active partition will have an asterisk * next to it. To set some partition as active, you can do:
```
sudo fdisk /dev/sda
```
Press "a", then select a primary partition to make active (type the partition number), then "w" to write the change. Let us know how it goes. :)

---

### Post by Ugeen on 2008-10-25
Sorry for posting here.  I thought that I posted on another thread. I had about 20 threads open at that time.  Now, I wonder which one this was meant for.

Again, I'm sorry for any confusion that may have cause.
--Ugeen

---

### Post by vanadium on 2008-10-25
Ugeen, you are interfering in a thread where we try to help shamusl. Your intervention might confuse the thread. You are welcome to open a new thread for your specific problem.

---

