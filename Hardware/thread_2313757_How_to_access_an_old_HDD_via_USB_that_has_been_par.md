---
title: "How to access an old HDD via USB that has been partitioned as dual-boot"
date: 2016-02-15
forum: Hardware
---

### Post by mangolassi on 2016-02-15
Hi everybody,

I used my old laptop as a dual-boot device (one partition Ubuntu, one partition Windows 8). It got broken, so I have to retrieve my data with a USB connector. Fortunatelly I still have one of those from using another old HDD as external storage. 

Now here's my problem: The USB connection works fine but the file explorer doesn't show any content. I think that might be due to the fact that there are several partitions on the hard drive.  Is there a way to access the files?

---

### Post by yancek on 2016-02-15
To access them, you need to first create a mount point then mount the partition.  Are you using a Live CD/flash drive?  Boot whatever you are using and open a terminal and run:  sudo fdisk -l(Lower Case Letter L in the command) to show the partitions on the drive.  If the data you are looking for is on sda1 do the following in sequence:

sudo mkdir /mnt/sda1
sudo mount -t ext4 /dev/sda1 /mnt/sda1

This should enable you to access the data.  Can't give you any more specifics due to the lack of information you posted.

---

