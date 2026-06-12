---
title: "Editing mount point of a partition"
date: 2008-11-24
forum: General Help
---

### Post by terabit8 on 2008-11-24
I have 3 partitions: a windows, ubuntu and a data partition.

When I installed intrepid 64bit I chose to mount the entire data partition in /home.
Now I want to have a seperate partition again instead of mounting it, how can I do that?

Thx in advance.

fstab output:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=a4e55cae-1777-4f85-be99-193a2a547dbe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=75b3a860-3682-4b72-a784-003ff1656d70 /home           ext3    relatime        0       2
# /dev/sda5
UUID=a00e0ccb-588b-49c9-a2d7-f30b67f3b9d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by AAOFan on 2008-11-24
You want to separate home from the old data partition? I think I understand what you are looking for.

You want a Windows Partition, Ubuntu Partition, and a Share Partition, but you don't want Ubuntu storing home settings and files to the Share partition anymore?

What you're going to need to do is make a whole new partition via booting off of a LiveCD and use qtparted to resize the home partition and make the new Share.

Use this command to install it if it isn't installed.```
sudo apt-get install qtparted
```

I would make the new Share partition FAT32 for Windows readability.

Once you've created the partitions the way you want, just move everything you want to share over to the share partition. Is this what you were looking for?

---

### Post by terabit8 on 2008-11-24
> **AAOFan said:**
> You want to separate home from the old data partition? I think I understand what you are looking for.

You want a Windows Partition, Ubuntu Partition, and a Share Partition, but you don't want Ubuntu storing home settings and files to the Share partition anymore?

Yes, I want to seperate that partition so when I go to 'computer' in nautilus I see all 3 partitions.

When installing intrepid I set the mount pount of /dev/sda2 (the data partition) to /home in this step (illustration, not my config) and I want to 'undo' that.
[IMG]http://www.shivaranjan.com/shivaupload/windowslivewriter/UbuntuLinuxInt.10InstallationWalkThrough_10AB/ubuntu_linux_installation_7_thumb.png[/IMG]

> **AAOFan said:**
> 
What you're going to need to do is make a whole new partition via booting off of a LiveCD and use qtparted to resize the home partition and make the new Share.

Use this command to install it if it isn't installed.```
sudo apt-get install qtparted
```

I would make the new Share partition FAT32 for Windows readability.

Once you've created the partitions the way you want, just move everything you want to share over to the share partition. Is this what you were looking for?
Problem with that solution is that the data partition is full of precious data that I don't want to lose.

---

### Post by easoukenka on 2008-11-25
Parted is a bit dangerous if you got important data I have personally lost data because of this program and it does warn you its not gauranteed.

Best thing would be to backup its a risky business

---

### Post by AAOFan on 2008-11-25
If you have room on your windows partition you could always copy it there first and then resize the home partition.

---

### Post by terabit8 on 2008-11-26
> **AAOFan said:**
> If you have room on your windows partition you could always copy it there first and then resize the home partition.
Not an option, the windows partition isn't large enough.

My problem is solved however but I can't explain how in detail since it was a friend (and experienced linux user) of me who solved it with vnc.

I had to boot from the live cd, create a home diretory on ubuntu partition, copy the home directory contents from the data partition in it, make ubuntu use that new folder and uncomment the /dev/sda2 (data partition) in the fstab file.

That is how he did it, the tricky part (wich I could not do) is how to make ubuntu use that new folder. If you just uncomment that mount point in the fstab-file ubuntu doesn't know where the home directory is.

---

