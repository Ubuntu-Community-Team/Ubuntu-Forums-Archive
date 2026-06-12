---
title: "unalloted hard disk space"
date: 2011-07-07
forum: Hardware
---

### Post by malakar.subhendu on 2011-07-07
I have windows as my default operating system and later used fedora as dual boot in an extended partition of 137gb. but since i installed ubuntu i am not able to use the partition. This problem is not due to ubuntu as i am not able to format it through windows also. please help, i am running out of disk space.

---

### Post by malakar.subhendu on 2011-07-07
using GParted the following was the output:
> **It is not possible to create more than 4 primary partitions**
If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first.


---

### Post by ajgreeny on 2011-07-07
Can you show us a screenshot of your gparted window, with some indication from you of what the four partitions contain, if it is not already obvious from their filesystems.

It sounds as if you may need to clone a partition then delete it and make a single extended partition in the space in order to add further new ones, but the screenshot should make things a lot clearer.  You may later be able to restore your cloned partition if it is needed.

---

### Post by malakar.subhendu on 2011-07-07
the screenshot is:[ATTACH]196929[/ATTACH]

/dev/sda2 is the windows partition.
/dev/sda3 is my personal partition.
/dev/sda4-/dev/sda7 is the linux partition.

---

### Post by ajgreeny on 2011-07-07
At the present time there is nothing showing in sda3, your ntfs personal partition.  If I have misread that, just backup any data etc etc to a usb drive and then, using a live CD/USB-gparted delete sda3 partition.  This will leave 335GB unallocated space.

Still with the live session-gparted, enlarge the current sda4, an extended partition, to include all the unallocated space right to the end of the disk.

Now in the unallocated space you can make as many logical partitions as you need to use for new linux OSs, or any other use you wish to put them to.  You do not yet seem to be running out of disk space, so I wonder what exactly you are trying to do.  Tell me more, please.

---

### Post by malakar.subhendu on 2011-07-07
I had around 100gb of movies which i had to delete to get the extended partition.


Is there no way to change the primary partition to extended partition?

---

### Post by ajgreeny on 2011-07-08
> **malakar.subhendu said:**
> I had around 100gb of movies which i had to delete to get the extended partition.


Is there no way to change the primary partition to extended partition?
Only by cloning, doing whatever you need to your partitions, and then restoring your clone to a new logical partition.

---

