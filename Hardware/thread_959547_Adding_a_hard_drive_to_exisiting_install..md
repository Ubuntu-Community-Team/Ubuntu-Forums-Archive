---
title: "Adding a hard drive to exisiting install."
date: 2008-10-26
forum: Hardware
---

### Post by Drezliok on 2008-10-26
I lost my server last week, hardware failure. I've tested the hard drive and it's fine, boots up into Xubuntu like it belonged there.

Well it doesn't lol. I need to mount it into my Ubuntu Desktop permanently so I can access my files once more.

Step 1:
Mount the drive and add it to the fstab.
Step 2:
Change the file ownership to my own.

How do I do Steps 1 and 2?


Thank you all for your time.
Drezliok

---

### Post by francisc1701 on 2008-10-26
See [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/AutomaticallyMountPartitions#Mounting partitions with the script") for step 1.

You can change the ownership of files with chown. Type "man chown" to learn how to use it.

---

### Post by cariboo on 2008-10-26
It depends on where you want to mount the drive. First thing you have to do is to find the blkid of the drive:

```
sudo blkid
```

You should get an output something like this:

```
sudo blkid
[sudo] password for jim: 
/dev/sda1: UUID="7E002ED0002E8F69" TYPE="ntfs" 
/dev/sdb1: UUID="3311c01c-be41-4fa7-962e-987f0123812d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="7befef38-ee49-3bbd-dbe5-214fc9cb4646" 
/dev/sda6: UUID="efccc4e7-3273-43d3-871c-1eb69aeaaa27" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="cb1960af-93d6-4dc7-aa05-6da60cd280e3" TYPE="ext3" 
/dev/sdb2: UUID="3d4a0ca8-b260-456b-82a5-70f71afda09e" SEC_TYPE="ext2" TYPE="ext3"
```

find the blkid of the disk you are going to add to /etc/fstab.

For examples sake I will use /dev/sdb1. Open your favourite text editor as root, press Alt-F2 and type:

```
gksu gedit /etc/fstab
```

Then using my example add the following lines:

```
#/dev/sdb1
UUID=3311c01c-be41-4fa7-962e-987f0123812d /media/test     ext3   realatime  0    2
```

mount the drive:

```
sudo mount /media/test
```

then change the permissions of /media/test:

```
sudo chmod -R 777 /media/test
```

You should now be able to access your information on the drive, and it will automount at boot.

Jim

---

