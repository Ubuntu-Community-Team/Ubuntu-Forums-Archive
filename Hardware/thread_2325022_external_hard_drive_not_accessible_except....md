---
title: "external hard drive not accessible except..."
date: 2016-05-18
forum: Hardware
---

### Post by wihenao on 2016-05-18
Hi. 

When I reboot my machine, my external hard drive becomes inaccessible. However, if I go to files and click on it, it becomes accessible all of a sudden.

So every morning I have to click on it, in order to start my work day. Anybody has any ideas?

Thanks a lot.

---

### Post by ajgreeny on 2016-05-18
> **wihenao said:**
> Hi. 

When I reboot my machine, my external hard drive becomes inaccessible. However, if I go to files and click on it, it becomes accessible all of a sudden.

So every morning I have to click on it, in order to start my work day. Anybody has any ideas?

Thanks a lot.
So am I right in thinking it is not inaccessible but just not mounted?  If you can mount it simply by clicking it in the file manager it is accessible and just needs to be mounted at boot by editing the /etc/fstab file.

Please show us the output of terminal commands ```
sudo blkid -c /dev/null
sudo parted -l
cat /etc/fstab
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by Bashing-om on 2016-05-18
wihenao; Hello;

Is the external drive always connected prior to firing the system up ?
Then you might consider explicitly mounting the external drive.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)

As guides on how/why to set this up to automount the external drive.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by yancek on 2016-05-18
If you want a partition on an external hard drive available on boot, you need an entry for it in the /etc/fstab file.  Not knowing the name of the drive/partition or the type of filesystem makes it difficult to be more specific.  You could post that info here and wait for suggestions or do an online search for entries in /etc/fstab which is the file you need the entry in.  What filesystem is it?  Linux, windows?

---

### Post by wihenao on 2016-05-19
It is datadrive. So all I have to do is edit the fstab...

wilmer@ioe-gpu:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="5609272e-b7d3-426f-9218-1667d59e4af5" TYPE="ext4" 
/dev/sda5: UUID="db33b349-0a65-4cbf-b05f-b4367a0c5541" TYPE="swap" 
/dev/sdc1: LABEL="datadrive" UUID="005ea273-8bcc-4e60-bdec-5cf79179f689" TYPE="ext4" 
/dev/sdb1: LABEL="fastdata" UUID="504b7d54-4a15-448d-8ac7-6be7c0c60a2b" TYPE="ext4" 
wilmer@ioe-gpu:~$ sudo parted -l
Model: ATA SAMSUNG SSD 830 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  222GB  222GB   primary   ext4            boot
 2      222GB   256GB  34.3GB  extended
 5      222GB   256GB  34.3GB  logical   linux-swap(v1)


Model: ATA SanDisk SDSSDHII (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      17.4kB  240GB  240GB  ext4


Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ext4


wilmer@ioe-gpu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=5609272e-b7d3-426f-9218-1667d59e4af5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=db33b349-0a65-4cbf-b05f-b4367a0c5541 none            swap    sw              0       0
wilmer@ioe-gpu:~$

---

### Post by Bashing-om on 2016-05-19
wihenao; Yeah !

If and the stress is IF this drive is always connected when you power the system up; Then :
Make up a mount point .
```

sudo mkdir /mnt/backup

```
Next is:
Edit the /etc/fstab file with admin privileges ( like unto similar gksudo gedit /etc/fstab )
Add:
```

##backup drive added 19May2016##
UUID= 005ea273-8bcc-4e60-bdec-5cf79179f689 /mnt/backup           ext4    defaults        0       0

```
save the file; exit the editor of choice; then  make sure the system accepts the edit:
```

mount -a

```

Mind ya, if this drive is not always connected .. will require that you use the appropriate mount options suitable to your use case . Then is homework time on your part to know what you want the system to do . Here the mount option(s) is  'defaults' where the drive is always connected.

By all means, if you do not fully understand what we are doing here you are invited to ask questions for clarification.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by wihenao on 2016-05-27
Thanks. That is great

---

### Post by Bashing-om on 2016-05-27
wihenao; Good deal !

Pleased it worked out for you.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

