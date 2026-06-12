---
title: "New HDD Read only"
date: 2013-10-22
forum: Hardware
---

### Post by gofes on 2013-10-22
Hello. Sorry for posting, I'm sure there is any easy solution but it's driving me mad and I can seem to find the solution. 

I've just installed a new HDD and it appears to be read only as myself, but root can write to it.

It's Disk /dev/sdd

(not really relevant but here we go)

> 
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000b575

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   112351231    56174592   83  Linux
/dev/sda2       112353278   117229567     2438145    5  Extended
/dev/sda5       112353280   117229567     2438144   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005c87d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953523711   976760832   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c7630

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953523711   976760832   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.



Also is "Partition 1 does not start on physical sector boundary." something else I should be worrying about?

---

### Post by gofes on 2013-10-22
I've made it worse

Now I can only mount wit root

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdd1 on /media/sdd1

---

### Post by oldfred on 2013-10-22
How did you partition it? With gparted or with gdisk?
       sudo gdisk -l /dev/sdd

If you have not installed gdisk run this first
sudo apt-get install gdisk

Is is permissions & ownership. Are you mounting automatically with Nautilus or have you added entries into fstab?

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Make sure unmounted first.

 sudo mkdir /mnt/data
sudo mount /dev/sdd1 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

Do you have just one monster partition? Or are you planning on having more than one to make it easier to backup or recover if one is damaged?

---

### Post by gofes on 2013-10-22
I used Gparted 
Didn't even have gdisk installed!

Currently Fstab looks like this

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=6c394387-0948-406a-9e06-d22bbd658b05  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=e03091b3-e5fa-45a5-82b4-95320e669b34  none         swap  sw                   0  0  


Currently I have sda - system
sdb - storage
sdc - storage
*new* sdd - storage

sdb and sdc don't mount on boot up, I just clicked on them in nautilus if I wanted them although I see no reason why I shouldn't add them to the fstab.

I was planning to leave the new sdd as one monster partition. I formated it as GPT Partition Table, (ext4) could the GPT be having an effect none of the other drives are.

The mount point for b and c is /media/sdc1 not /mnt although i do have that folder, should this be changed as well?

---

### Post by oldfred on 2013-10-22
You can create a lot of discussion (argument) on whether to use /media or /mnt. I prefer /mnt only because it does not show in Nautilus' left panel. But I am linking all folders in my mount into /home so I do not want duplicate entries. But if /media works for you that is ok too.

I have two gpt drives (smaller) and two MBR(msdos) drives, so mixed drives should not be an issue.

This is how I edit my fstab, following the templates from Morbius1.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

---

### Post by gofes on 2013-10-22
I've tidied up my fstab

All 3 drives now mount on boot up

But the new one (d) still wont let me write to it, only root can.
I'm sure I need to add myself to a user group or something?

The only thing I can find all seem to relate to nsfs formatted drives.

---

### Post by oldfred on 2013-10-22
See post #3 but now change to where you have mounted with fstab.

sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data

---

### Post by gofes on 2013-10-22
Yes, all sorted!

---

