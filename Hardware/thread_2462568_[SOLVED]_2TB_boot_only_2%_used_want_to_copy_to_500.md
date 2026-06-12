---
title: "[SOLVED] 2TB boot only 2% used want to copy to 500GB how?"
date: 2021-05-23
forum: Hardware
---

### Post by Raymond Day on 2021-05-23
I want to use the 2TB boot drive on another system. this is a over kill for the boot drive. So want to put a 500GB on it.

A df shows it like this:

/dev/sdn2                            1.8T   23G  1.7T   2% /

I did a DD copy with a live ubuntu desktop and it shows no partitions then.

After it booted so I did a DD copy as it was running but same no partitions.

Guess it starts to use the drive at the end of it not the start so a DD copy don't get the Data.

How can I copy this 2TB that only 2% is being used to a 500GB drive? Is that some command to do it?

Maybe shrink the drive to 500GB then can copy it. But I don't know how to shrink it if you can.

Did a parted on the 500GB it looks like this:

> parted /dev/sdb
GNU Parted 3.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Error: Invalid argument during seek for read on /dev/sdb
Retry/Ignore/Cancel? r
Error: Invalid argument during seek for read on /dev/sdb
Retry/Ignore/Cancel? i
Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel?
OK/Cancel? OK
Model: ATA WDC WDS500G2B0A- (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:
(parted)


Thank you.

-Raymond Day

---

### Post by oldfred on 2021-05-23
You cannot use dd to copy from larger to smaller as it also copies blank or unused space. And even if 2% used it is not necessarily at beginning of drive. And gpt has essential backup partition table at end of drive.

Better to just do new install to 500GB drive, then copy /home.
If not same system, best not to copy /etc unless you know some file is not system dependant.
And you can export list of installed apps.

Or better is to do new install & restore from your normal backup. Good test that backup includes everything your need when your drive fails.

Your will need Ubuntu live installer, to repair grub if moving drive to new system.

---

### Post by Raymond Day on 2021-05-24
Did test gparted but it said if shrink could loose the data. So I did not do that. I guess gparted don't move the data.

So loading fresh and had to copy the /etc/fstab from the old drive. So my drives are mounted again like they were.

Now have to copy the database how do I do that from the old drive?

-Raymond Day

---

### Post by oldfred on 2021-05-24
You cannot copy all of fstab as / , /home and swap (if you have those) will have new UUIDs.
But you can copy any additional entries for other partitions. I use my new install script to automate it.

My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/My](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/My) backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 

I found I have to install dselect to make it work to add applications from the list.
I now also use my script to add most of the applications I want.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[https://ubuntuforums.org/showthread.php?t=2440020](https://ubuntuforums.org/showthread.php?t=2440020)
[https://ubuntuforums.org/showthread.php?t=2392127](https://ubuntuforums.org/showthread.php?t=2392127)

Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

My rsync to another drive is not really a backup, but just a current copy and it overwrites older versions & deletes, deleted files. But I do similar rsync to multiple flash drives, and also put some files & photos on DVDs as my real backup archives.

---

### Post by mastablasta on 2021-05-24
you can do it with clonezilla with -icds option:
[https://clonezilla.org/clonezilla-live/doc/11_lite_server/advanced/09-advanced-param.php](https://clonezilla.org/clonezilla-live/doc/11_lite_server/advanced/09-advanced-param.php)

but you need to know what you are doing.

---

### Post by Raymond Day on 2021-05-26
[I seen this post how to do it]("https://askubuntu.com/questions/47409/shrink-a-partition-without-losing-data") but backing up the drive now just incase something goes wrong.

Looks like it's easy just use this.

resize2fs /dev/sdx2# 500G

Not on the 1st partition that is the boot but on the 2nd large one.

Then can use gparted with out it saying will loss data.

Will take some time to copy this to test if this works.

-Raymond Day

---

### Post by Raymond Day on 2021-05-28
It worked and I used Gparted to shrink it. It still said my loss data. I said do it any way because on a backup.

Put it on my server and booted from it and it came up worked just like it use to.

So I booted a live USB Desktop and did a DD copy. It did it till it said no space left on device.

But booting it just goes to a command line that seems like only for disk things infogram something like that.

So I guess DD is the wrong way to copy it. Maybe just need to copy the 2nd partition?

How can I copy this to my 500GB SSD now that it is that size on a partition on a 4TB HDD drive.

Here is some commands that my help to copy this. Looks like I DD copied it and it don't have any partitions. Not sure what went wrong.

```
root@rayday:~# df -h /dev/sdn2
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdn2       458G   24G  411G   6% /
root@rayday:~# df -h /dev/sdb
Filesystem      Size  Used Avail Use% Mounted on
udev             16G     0   16G   0% /dev
root@rayday:~# fdisk /dev/sdb

Welcome to fdisk (util-linux 2.34).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): p
Disk /dev/sdb: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: WDC WDS500G2B0A-
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start        End    Sectors Size Id Type
/dev/sdb1           1 4294967295 4294967295   2T ee GPT

Command (m for help): quit

root@rayday:~# fdisk /dev/sdn

Welcome to fdisk (util-linux 2.34).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

The backup GPT table is not on the end of the device. This problem will be corrected by write.

Command (m for help): p

Disk /dev/sdn: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: ASM1156-PM
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 9E7F787A-2B3B-443C-A814-FE263D9B6036

Device       Start       End   Sectors   Size Type
/dev/sdn1     2048   1050623   1048576   512M EFI System
/dev/sdn2  1050624 977373183 976322560 465.6G Linux filesystem

Command (m for help): quit

root@rayday:~#
```

-Raymond Day

---

### Post by oldfred on 2021-05-28
Did you try a new install which will give you correct partitions?
Then use rsync to copy your data from /home and any other folders you need?

New install is about 10 min to SSD once live installer is booted into RAM & gpt partitions already created.
Reinstalling apps can take a bit depending on your Internet speed.
Rsync copy can be quick if internal network is fast.

What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&)

---

### Post by SeijiSensei on 2021-05-29
Don't try to copy the data at the bit level with something like dd if you're changing size. Partition the target disk the way you want and format the newly-created partition as ext4. Then mount the drive into the filesystem and use a program like rsync that copies files and directories.

---

### Post by Raymond Day on 2021-05-31
I got it working.

The **resize2fs**  command worked took about 10 min. I resized it to 500GB.

Used a live Ubuntu USB boot desktop and used Gparted.

Had to resize the source drive to smaller then 500GB then could just use copy and paste the **small boot partition** and **big main partition**.

It booted and is just like it was with the 2TB SSD that was booting from now it's got a 500GB SSD booting from.

It worked very good with Gparted.

It would not let me paste it till it was a smaller size. I all so said in Gparted to expand it to the full size on the 500GB SSD.

-Raymond Day

---

