---
title: "Ntfs"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by silvermonkeyfeed on 2009-02-15
hello i just installed ubuntu on my acer aspire one and it comes with windows xp installed and it is using the ntfs file system and ubuntu says it can not recognize the files on the partition so i need to know if any body knows of a software that can change the file system without formating the partition

---

### Post by oldos2er on 2009-02-15
Which version of Ubuntu? 8.xx should be able to read NTFS partitions "out of the box." Was the NTFS partition shut down cleanly last time it was used?

---

### Post by silvermonkeyfeed on 2009-02-15
no it was not. ubuntu 8.10

---

### Post by oldos2er on 2009-02-15
> **silvermonkeyfeed said:**
> no it was not. 

 That's the reason Ubuntu's refusing to mount it; it attempts to preserve your data. Boot back into Windows and do a clean shutdown.

---

### Post by silvermonkeyfeed on 2009-02-16
but i did not install the boot loader for the windows partion so it will not boot into windows.

---

### Post by MasterProg on 2009-02-16
Try forcing mount.

Firstly, find out which device is your NTFS partition:
```
sudo fdisk -l
```
Then create some mount point:
```
sudo mkdir /media/**ntfs**
```
After that mount it (replace **disk-device** with your partition):
```
sudo mount -t ntfs-3g /dev/**disk-device** /media/**ntfs** -o force
```

After that you will (should) be able to use the partition as you would normally.

---

### Post by oldos2er on 2009-02-16
> **silvermonkeyfeed said:**
> but i did not install the boot loader for the windows partion so it will not boot into windows.

 How are you booting Ubuntu?

---

### Post by Mark Phelps on 2009-02-17
> **silvermonkeyfeed said:**
> hello i just installed ubuntu on my acer aspire one and it comes with windows xp installed and it is using the ntfs file system and ubuntu says it can not recognize the files on the partition so i need to know if any body knows of a software that can change the file system without formating the partition

To go back to your original question ...

There are utilities available to change FAT32 partitions to NTFS partitions -- for MS Windows -- while retaining the data, but I'm not aware of any that can change FAT32 or NTFS to Ext3 without erasing the data.

If you didn't already create a second partition for Ubuntu, I'm presuming that you installed Ubuntu inside MS windows using Wubi. Is that correct?

So, is you real question about how to replace your machine with an Ubuntu-only installation without reinstalling from scratch?

---

