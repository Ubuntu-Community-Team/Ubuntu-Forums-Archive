---
title: "Partition assistance needed!"
date: 2017-01-04
forum: Hardware
---

### Post by 69clifford on 2017-01-04
I just purchased a new 4 TB Seagate HDD. I went to the partition manager and changed the partition's format from NTFS to ext4. Ever since I did this, I cannot write to the drive. It also doesn't seem to be mounting properly. I attached a screenshot of the partition info.[ATTACH=CONFIG]273028[/ATTACH]

Any ideas why I'm having issues?


EDIT: Is it normal to have to change the directory permissions after creating a new partition?

---

### Post by Autodave on 2017-01-04
Is this the only HD in the system, or is it the second, third, etc?

---

### Post by 69clifford on 2017-01-04
> **Autodave said:**
> Is this the only HD in the system, or is it the second, third, etc?

Attached is a screenshot of the drives and partitions on my PC. My internal drive has been funky so I've been running off an external SSD. Then I have a SD card and the external drive.
[ATTACH=CONFIG]273034[/ATTACH]

---

### Post by oldfred on 2017-01-04
Are you sure you only want one partition on a 4TB drive? If recording video you may.
But fsck or backup of one partition that is that large may take forever.

I also label all partitions. Some I do not mount in fstab, so then when automounted they have a label I understand rather than some long UUID which I do not know what it is. You can label with gparted when creating partitions, with gnome Disks or command line. 
Do not know Kubuntu's partition tools, but would expect it also can add labels.

You do need to set ownership & permissions with any new partition.

All new partition tools should set alignment correctly. And it is important for new 4K drives and SSDs. Old drives not so critical.

If drive is not internal, are you sure your hard drive caddy/case supports large or gpt drives? We have seen users have issues with low cost or older caddy. 

If not mounting with fstab, I create mount point, mount partition and then set ownership & permissions. 
       #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

---

### Post by eionmac on 2017-01-07
Live Linux use. When in formatting problems, I tend to always use an external Live Linux , normally i use Gparted in the Knoppix Live distro. Regards Eionmac

---

