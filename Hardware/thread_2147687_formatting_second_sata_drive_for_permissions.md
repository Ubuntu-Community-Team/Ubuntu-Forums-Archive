---
title: "formatting second sata drive for permissions"
date: 2013-05-22
forum: Hardware
---

### Post by Capetownlad on 2013-05-22
Hi 
I am using Ubuntu 10.04 
I have a problem with a second sata drive I have added. I just want to use it as an empty drive to copy files to. I have formatted it to ext4 but when I try copy to it I get the error, permission denied. Any advice would be appreciated.

output of fdisk -lu :

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001d4eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   957124607   478561280   83  Linux
/dev/sda2       957126654   976771071     9822209    5  Extended
/dev/sda5       957126656   976771071     9822208   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c3f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641   83  Linux

and

output of cat /etc/fstab:

/etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=04fa0496-3ee4-4d9f-a267-f0a508de9377 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d415364a-96f2-47f0-9b51-7eb4acec31eb none            swap    sw 


Hope this is of some help?

- capetownlad

---

### Post by coffeecat on 2013-05-22
We don't have quite enough information to give a full answer, but I think I can get you there. What you need to do is to:

[list=1][*]Mount the sdb1 partition.
[*]Change the ownership of the sdb1 filesystem to give you permission to write to it[/list]

The second is achieved by running the chown command on the mountpoint, which has the curious and useful effect of chown-ing the fileystem, if it is mounted.

Open a Nautilus file browser and click on the 320GB partition which you should see in the left pane. If it has a partition label, then you will see this. If not, something like "320GB filesystem". The file browser will mount the partition and show its contents in the main pane of Nautilus. You don't need to do anything further with the file browser just yet.  

Now open a terminal. Run this command:

```
mount
```

Look for the line referring to /dev/sdb1. Make a note of the mountpoint. It will be something like, /media/very-long-string.

Now, in the terminal:

```
sudo chown yourusername: /media/very-long-string
```

Obviously, substitute your username for yourusername. Don't forget the trailing colon after yourusername - that's to assign ownership with your default group - and change /media/very-long-string to whatever it should be.

Now try copying files to the mounted partition. They should copy OK.

One slight extra if you want others to be able to access the mounted partition is this command:

```
sudo chmod 777 /media/very-long-string
```

Not strictly necessary if you are the only user, and it has the security disadvantage of giving read-write access to the world and its grandmother.

Post back if that doesn't work, and if you do, post the full output of the mount command.

**EDIT**: I've just noticed that you are using the now-obsolete version 10.04. I've adjusted the commands to make allowance for the way 10.04 automounts partitions, with some differences from the way more recent and current versions of Ubuntu do so, but I am going from memory. Again, post back if you have nay problems, but bear in mind that 10.04 is no longer supported. You need to rethink about upgrading.

---

### Post by ajgreeny on 2013-05-22
I presume sdb is your second sata drive giving you the problem, which is simply one of permissions. I note also that it is not included in your /etc/fstab file so is not mounted at boot, so for simplicity I suggest you label the partition to sdb1 with ```
sudo tune2fs -L sdb1 /dev/sdb1
```which means that the partition will always mount at /media/sdb1.  Tyhen you need to make a folder /media/sdb1 with command ```
sudo mkdir /media/sdb1
``` then add the following two lines to /etc/fstab
```
# Disk 2 on /dev/sdb1 mounted at boot
UUID=[COLOR=#ff0000]2a1a9b57-4d0a-4570-974f-d6114fb25ef1[/COLOR] /media/sdb1           ext4    defaults,relatime        0       2
```Change the UUID (in red) to that of your partition which you can get from ```
sudo blkid -c /dev/null
```
You will also need to give yourself permission to write to the partition either with a chown command to your username on the mountpoint ```
sudo chown *username:username* /media/sdb1
``` or using general chmod 777 permissions which gives everybody full permissions on that mount point, perhaps less secure.

Come back again if that does not make full sense to you and I'll try to make it a bit clearer.

---

### Post by Capetownlad on 2013-05-23
Thanks for the replies. I will attempt this later when back from work

---

### Post by Capetownlad on 2013-05-23
Thank you both for the replies and help. I have started with coffeecat's  advise merely due to chronogical order and immediately I have a problem.  The drive shows as 320Gb file system but again can't mount it. The terminal command 'mount' also fails with error message: 'only root can mount /dev/sdb1 on /media/mynewdrive'. I think I've really ruined everything! 
What other information can I give you so 'we' can solve this ?

---

### Post by Capetownlad on 2013-05-23
[**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")  Thanks for your guide. I have labeled the partition as you suggested.  The next step of making the folder gave me this return 'sudo mkdir  /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists' 
So I have continued to the end and run the chown command. 
Is that it or is there more to do?

---

### Post by Capetownlad on 2013-05-23
deleted

---

### Post by Capetownlad on 2013-05-23
[**[COLOR=#000000]deleted[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")

---

### Post by ajgreeny on 2013-05-24
> **Capetownlad said:**
> [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")  Thanks for your guide. I have labeled the partition as you suggested.  The next step of making the folder gave me this return 'sudo mkdir  /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists' 
So I have continued to the end and run the chown command. 
Is that it or is there more to do?
That could well be all that is needed.

Try it out and you'll soon see if there is still a problem with writing to that disk/partition as user.

---

### Post by Capetownlad on 2013-05-25
I started again from partitioning and followed the advice given and very pleased to say its now behaving as expected. Thanks so very much for the help here.

---

