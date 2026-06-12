---
title: "partitions and permissions"
date: 2014-06-19
forum: Hardware
---

### Post by kakashi_12 on 2014-06-19
I have a couple of questions. First off, when installing Linux manually; what do they mean by the mount point? Is that where GRUB is installed? The difference between mounting is / or /home or /root, etc. And WHERE that actually is on the drive. If I'm doing a multi-boot system, where should the mount point be.

Secondly, I have been recommended to create an Extended Partition with a Logical Volume to store all my data. Since I have multi-boot systems. Which is not a bad idea. But what do I do in my case?
I use NTFS permissions in Windows. I'm pretty sure Linux does not notice NTFS permisssions. Can I set Linux permissions on the same drive/volume as the data that already has NTFS permissions on it?
Or is there a way I can allow a user to ONLY be able to mount one particular volume and not all of them? I already have Linux set now so that Desktop Users can not mount volumes. Don't want them touching the Windows system files, etc.
I don't really have money to implement a NAS on the network right now. Any thoughts or ideas?

---

### Post by yancek on 2014-06-19
Mounting basically means to give access to.  The mount point for a filesystem in Linux is "/" the forward slash.  That is the base or root of the filesystem, not to be confused with the root user.  If you have a system installed and create a separate partition for personal data such as pictures, movies in order to 'access' them you would have to mount that partition to a mount point.  Example:  sudo mkdir /mnt/movies.  That creates the mount point.  In order to access the movies, you need to mount them eithe with the mount command or by putting an entry in the /etc/fstab file.

>  Is that where GRUB is installed?

No.  A small part of Grub code usually goes into the master boot record but the vast majority of the files/code for Grub are on the system partition.

> If I'm doing a multi-boot system, where should the mount point be.

The mount point for what?  If you want to mount system B from system A, you can create a mount point and mount manually or put a proper entry in the /etc/fstab file.  When you are installing a Linux OS, the mount point should bye "/", the forward slash, symbol for root of the filesystem.

I'll leave the rest of your questions for someone more knowledgeable.

---

### Post by kakashi_12 on 2014-06-19
The mount point to install the Linux/Ubuntu OS. So / or root is at the beginning of the partition then? This is also the first part of the filesystem when going to 'my computer' then select the 'filesystem' drive?

---

### Post by grahammechanical on 2014-06-19
When we chose the Something Else option we get a screen (Installation Type) where we have to select a partition where we want Ubuntu to be installed. We select the partition and we then click Change and a small dialog appears. We go to the panel labelled Use As and select the file system. It usually is Ext4. Then we tick the box labelled format and then go to the panel labelled Mount Point and select / as the mount point. Now we can click OK and that brings us back to the Installation Type screen.

If we want to have a separate home partition instead of a /home folder in the / partition, then we repeat the process but this time the mount point will be /home. Do not confuse setting a mount point as part of a Something Else install of Ubuntu and mount points of partitions in an existing working installation.

As regards Extended and logical partitions that all depends if the motherboard uses a BIOS or UEFI boot system. With a BIOS boot system we are only allowed 4 primary partitions. Which is very limiting but we can set one of those 4 primary partitions to be a special primary partition called an Extended partition. Then inside that Extended partition we can create Logical partitions. Any number of them until the Extended partition space is used up. And so we overcome the 4 primary partition limitation.

With a UEFI boot system a different form of partition is used called GPT (GUID Partition Table - Globally Unique Identifiers Partition Table) which does not limit the number of partitions.

You may or may not need to create an Extended Partition and inside it logical partitions. It all depends on whether you have BIOS with the partitioning information stored in the Master Boot Record (MBR) or UEFI which uses GPT.

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)


You will also find that users can have access to folders and files that they have created and they can both read and write to those files and also delete them. But as regards to folders and files that other users have created they may be able to access the files to read the contents but they cannot write to the file or delete unless the permissions on the file are changed by the Administrator to allow those users to do that. It is also possible for the Administrator to deny access to folders and files to any user who is not the owner of the folder or file.

Regards.

---

### Post by kakashi_12 on 2014-06-20
I tried to dual boot Ubuntu with an existing Win7 install. But it failed and made Win non-bootable. I choose / as the mount point too, so not sure why it failed. I thought maybe I had the mount point wrong.

So I can use permissions in Windows and Linux then for the same logical partition? ok, i'll have to try that out.

---

