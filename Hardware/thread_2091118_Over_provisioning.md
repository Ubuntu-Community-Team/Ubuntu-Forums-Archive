---
title: "Over provisioning"
date: 2012-12-04
forum: Hardware
---

### Post by WanchoPiskado on 2012-12-04
Hi,

I have Ubuntu 12.04 64bit installed on a Samsung 830 SSD of 128GB. I learned that over provisioning is a good thing to do. I have this question thoug. Do i need to create an unallocated partition to over provision? Or will the SSD automatically use the free space on my SSD? I do have enough free space on my SSD. So creating an allocated partition will be no problem. I just don't know if this is necessary.

---

### Post by Statia on 2012-12-04
> **WanchoPiskado said:**
> 
I learned that over provisioning is a good thing to do. I have this question thoug. Do i need to create an unallocated partition to over provision? Or will the SSD automatically use the free space on my SSD? I do have enough free space on my SSD. So creating an allocated partition will be no problem. I just don't know if this is necessary.

If you don't want to meddle around later with resizing partitions, the wise thing to do is oversize the partitions you are going to make. Give them at least 33% more than you anticipate they will need. It is recommended filling essential partitions not over 75%.

Say you expect to need 12GB for your root partition, make the size of the partition 16GB.
If you would indeed fill 12GB, disk usage is 12/16 = 75%.
This gives you some breathing room in case you need to move stuff around.

---

### Post by WanchoPiskado on 2012-12-04
Hi Statia!,

Thank you for your reply. I already made an extra 12 GB unallocated partition for over provisioning. I just wanted to know if this is necessary, of that the SSD would automatically use the free space on my SSD.

Are you from St Eustatius? Me here in Curacao.

---

### Post by Statia on 2012-12-04
> **WanchoPiskado said:**
> 
Thank you for your reply. I already made an extra 12 GB unallocated partition for over provisioning. I just wanted to know if this is necessary, of that the SSD would automatically use the free space on my SSD.

Are you from St Eustatius? Me here in Curacao.

Hi WanchoPiskado,

The SSD will not automatically grow partitions when they start to fill up. Also, the 12GB unallocated partition will not automatically be used. You could use it later to donate space using gparted, but that is not the most trivial task.
I would recommend planning your partitioning scheme out before installing, making all partitions about 33% bigger than you expect to need.

I'll give you an example with relevant sections from my setup:

```
Filesystem                        Size  Used Avail Use% Mounted on
/dev/sda5                          29G   13G   15G  47% /
/dev/sda1                         179M   64M  106M  38% /boot
/dev/sda3                          27G  4.9G   21G  20% /mnt/data
/dev/sdb1                         450G  191G  236G  45% /home
/dev/sdb6                         704M   17M  651M   3% /srv
/dev/sdb5                         1.2G  948M  208M  83% /var
tmpfs                             3.9G  8.0K  3.9G   1% /var/spool
tmpfs                             3.9G  120M  3.8G   3% /var/tmp
tmpfs                             3.9G     0  3.9G   0% /var/cache/apt/archives
tmpfs                             3.9G  228K  3.9G   1% /tmp

```/dev/sda is my 60GB SSD, /dev/sdb my 500GB HDD.
I wanted to reduce writes to the SSD (there is discussion whether this still is necessary for modern SSD's, but I just wanted to be on the safe side).
I choose to have the root filesystem on /dev/sda5, gave it about 30G and I am using 13G of that now, with everything and the kitchen sink installed. I could have made that smaller. If I would reinstall, I'd make it 18-20GB and give the rest to /mnt/data.
The rest of the SSD is a data partition that I could use for backup of data that does not change often. I keep a snapshot of a virtual machine there for instance.

I gave /boot a separate partition. I normally keep only two kernels on my system, so this one is more than big enough as well.

The parts of the system that have lots or writes I either gave separate partitions, or put in RAM (I have 8GB, which is plenty, under normal use I am hard pressed to fill even 2G). That would be mostly /var and /tmp.

/var could have been bigger as you see, but I keep it under control by running apt-get clean every now and then, deleting the crash reports in /var/crash and cleaning out /var/log every now and then. If I had to reinstall, I probably would not make a seperate /srv anymore and instead make /var 2G.
(Yeah, I should set up a cronjob to do that for me)

I used to live on Statia, but unfortunately, back in the rain and cold.

---

### Post by jwcalla on 2012-12-04
The Samsung 830 is already over-provisioned 7%, so there's really nothing else you need to do.

However, all free space is used for wear leveling, whether it's formatted or not.  Either way, even if you do want to put in a hard limit for yourself (though there's no need), you can use the tune2fs tool to reserve disk space without worrying about partitions.  The reservation can be changed at any time.  Note that by default, ext4 partitions have a 5% reserve.

---

