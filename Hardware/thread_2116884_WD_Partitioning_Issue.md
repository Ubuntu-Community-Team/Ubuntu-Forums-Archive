---
title: "WD Partitioning Issue"
date: 2013-02-17
forum: Hardware
---

### Post by maddy_in65 on 2013-02-17
I had purchased WD 1TB External drive, I partitioned it with gparted and created 1 NTFS and other EXT4 partition. However i am not able to use Ext4 parition, I cant paste any data in that volume, or create any folder there. I formated that drive with NTFS and no issues with this. I changes drive to logical, formated with ext3 but nothing worked. How do i use Ext4 volume.

---

### Post by sudodus on 2013-02-17
> **maddy_in65 said:**
> I had purchased WD 1TB External drive, I partitioned it with gparted and created 1 NTFS and other EXT4 partition. However i am not able to use Ext4 parition, I cant paste any data in that volume, or create any folder there. I formated that drive with NTFS and no issues with this. I changes drive to logical, formated with ext3 but nothing worked. How do i use Ext4 volume.

Can you mount the drive? If you can, how are you mounting it?

Can you identify the partition with the following commands (run one command line each time)

```
sudo fdisk -lu
sudo blkid
sudo df
cat /etc/fstab
cat /etc/mtab

```

I have too little information to know yet, but if you try to write or copy to the partition from Ubuntu, it should work, unless you don't have the correct permissions. Windows cannot read/write linux partitions (unless you install a special driver).

If you can, please ***list directory*** where you have the mount point and post it

If the mount point is /mnt
```
ls -l /
```
If the mount point is /media/something
```
ls -l /media
```

---

### Post by maddy_in65 on 2013-02-17
Thanks for the quick reply.
Here is the output of blkid command. sdb5 is ext4 formatted WD drive.

> 
sudo blkid
/dev/sda1: UUID="3ABE7ED7BE7E8B61" TYPE="ntfs" 
/dev/sda5: UUID="5527E6BE4A3FD342" TYPE="ntfs" 
/dev/sda6: UUID="147F839A7CB66569" TYPE="ntfs" 
/dev/sda7: UUID="eab51866-86d5-4588-abb8-0b781359ab43" TYPE="ext4" 
/dev/sda8: UUID="fdeb5539-8e95-467c-8368-f4338b456e31" TYPE="swap" 
/dev/sda9: UUID="449fc4cb-2a9d-4cf6-a1d0-03b604f5585f" TYPE="ext4" 
/dev/sdb1: UUID="6338D85A040DE6FF" TYPE="ntfs" 
/dev/sdb5: UUID="2104c690-8e7d-4263-b432-486680c40562" TYPE="ext4" 


and here is mount details

> 
ls -l /media/maddy
total 12
drwxr-xr-x 3 root  root  4096 Feb 17 11:36 2104c690-8e7d-4263-b432-486680c40562
drwx------ 1 maddy maddy 4096 Feb  4 10:08 5527E6BE4A3FD342
drwx------ 1 maddy maddy 4096 Feb 16 23:18 6338D85A040DE6FF



Also i have same problem on debian

---

### Post by carl4926 on 2013-02-17
If you give the partition a Volume Label
Eg: STORE

Then if your username is 'maddy'

```
sudo chown -R maddy STORE
```

---

### Post by maddy_in65 on 2013-02-17
Thank you so much. Solved the problem. Another question, do i need to run command every time i boot the system.

---

### Post by sudodus on 2013-02-17
> ```
ls -l /media/maddy
 total 12
 [COLOR="Red"]drwxr-xr-x[/COLOR] 3 [COLOR="RoyalBlue"]root root[/COLOR] 4096 Feb 17 11:36 2104c690-8e7d-4263-b432-486680c40562
 drwx------ 1 maddy maddy 4096 Feb 4 10:08 5527E6BE4A3FD342
 drwx------ 1 maddy maddy 4096 Feb 16 23:18 6338D85A040DE6FF

```

The [COLOR="Red"]permissions[/COLOR] show that only [COLOR="RoyalBlue"]root[/COLOR] has write access to that drive.

Use 'sudo command' to do these tasks

```
sudo chmod 755 'directory'
```
```
sudo chown user 'directory'
```

You can change either the permissions or the ownership or both to be able to write to the partition. If only you are supposed to use it, I suggest that you change the ownership of the whole partition (the mount point). If several people will use it, create subdirectories and give appropriate permissions to each of them, typically all permissions for the user (read,write,execute) but only read and execute for group,others. Finally change ownership for each of the subdirectories.

---

### Post by carl4926 on 2013-02-17
> **maddy_in65 said:**
> Thank you so much. Solved the problem. Another question, do i need to run command every time i boot the system.

If you mean chown
No

It's done.

---

### Post by sudodus on 2013-02-17
> **maddy_in65 said:**
> Thank you so much. Solved the problem. Another question, do i need to run command every time i boot the system.
No, it should be persistent and inherited to subdirectories

---

