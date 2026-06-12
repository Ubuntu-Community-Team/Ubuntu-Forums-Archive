---
title: "HD assignments"
date: 2016-03-01
forum: Hardware
---

### Post by Lappert on 2016-03-01
Up until a recent crash, I was running Kubuntu 14.04 on top of    a Ubuntu server install. I chose the server setup so I could Raid    two sets of drives. After the crash, I decided to forgo the Raid 1    setup, freeing up two drives.
    
    Former setup,
    
    [INDENT]2 X 250 GB SSD, Raid 1, mounted at / - mostly for the OS and /home
    2 X 2 TB drives, Raid 1, mounted at /opt - mostly data[/INDENT]
    
    Now, after discontinuing the Raid, and installing Kubuntu 15.10
    
    [INDENT]1 X 250 GB SSD, partition sda1, mounted at / - for the OS and /home
    1 X 250 GB SSD, partition sdb1, mounted at /media/sdb - data and    virtualbox
    1 X 2 TB drive, partition sdc1, mounted at /media/sdc - mostly data    and backup
    1 X 2 TB drive, partition sdd1, mounted at /media/sdd - mostly data    and backup[/INDENT]
    
    It took a bit of work to get the drives working as they were setup    for RAID and had md partitions. So cleaning the drives where they    could be mounted was a task. But that's mostly done.
    
    The problem I still have is the assignment of drives sdc and sdd.    They seem to be reversed and nothing I have tried can get them    working the say they should.
    
    **From fdisk -l**
    [INDENT]**Disk /dev/sdc**: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: dos
    Disk identifier: 0x1701d396
    
    Device     Boot Start        End    Sectors  Size Id Type
    /dev/sdc1        2048 3907028991 3907026944  1.8T 83 Linux
    
    **Disk /dev/sdd**: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: dos
    Disk identifier: 0x1701d392
    
    Device     Boot Start        End    Sectors  Size Id Type
    /dev/sdd1        2048 3907028991 3907026944  1.8T 83 Linux[/INDENT]
    
**from fstab**
    [INDENT]
/dev/sdc1    /media/sdc    sdc    ext4    defaults    0    0
    /dev/sdd1    /media/sdd    sdd    ext4    defaults    0    0[/INDENT]
    
    with similar output from gparted. Understand that sda and sdb are stable and show up where they should.

Here's the problem. The physical drive sdc, along with all of its content, shows up on /media/sdd. And the physical drive sdd shows up on /media/sdd.

I tried switching labels with e2label, but that doesn't solve anything.

As it is now, the physical drive /dev/sdc, the partition /dev/sdc1, the mount point /media/sdc and label sdc .... are all in alignment. But the drive and its contents shows up on /media/sdd.
Likewise, sdd shows up on /media/sdc.

I would very much appreciate any insight on how to fix this. Thank you.

---

### Post by weatherman2 on 2016-03-01
You aren't forced to to use these default label as mountpoints for the filesystem.  They were picked for you as placeholders.  Pick your own names.  You could call them /mnt/data1 /mnt/data2 /mnt/data3 . Or /mnt/virtualbox /mnt/data /mnt/backup.  Or whatever you want to call them.

(Notice how I changed from using /mnt instead of /media ?  When I manually mount partitions in fstab, I don't use /media - I leave that for the mounting of temporary and external devices you mount in the file manager.  /mnt is reserved as a place to mount partitions - but you can really use almost any mountpoint you wish.  You can make mountpoints at the top of the filesystem if you wish - just plain /virtualbox /data /backup.  It's up to you!)

Let's say you want to use /mnt/data1 /mnt/data2 and /mnt/data3 as your three mountpoints for the partition on each of the last three drives.  Then do this, in a terminal:

```

sudo mkdir /mnt/data1 /mnt/data2 /mnt/data3

```

Then use a text editor (with sudo) to edit the file /etc/fstab - replace the existing lines for the three and replace them with these:

Change the lines

```

/dev/sdc1 /media/sdc ext4 defaults 0 0
/dev/sdd1 /media/sdd ext4 defaults 0 0

```

to:

```

/dev/sdb1 /mnt/data1 ext4 defaults 0 0
/dev/sdc1 /mnt/data2 ext4 defaults 0 0
/dev/sdd1 /mnt/data3 ext4 defaults 0 0


```

Save the file then type:

```

sudo umount /dev/sdb1 /dev/sdc1 /dev/sdd1
sudo mount -a

```

The last command re-mounts everything in your /etc/fstab file - if it is successful then you will get no output from it.

Again you don't have to use "data1" etc. - make up whatever names you wish.

And finally...you might look at using UUID instead of the device identifiers like /dev/sdb1 etc.  The UUID is a unique code that corresponds to each partition.  The reason you use UUID is that if you switch your drives around (say you swap sda and sdb even by accident) it won't matter - the partitions still get mounted in the right places, because you are no longer referencing the device IDs that change when the drive order changes.  UUID is unique for each partition.

You can get UUID for each partition using the command "sudo blkid" .  Say the UUID of /dev/sdb1 turns out to be f6b1edce-a04a-4eeb-83c5-940c63be77a4 .  Then in your fstab file your line to mount (what is sdb1 at the moment would become):

```

UUID=f6b1edce-a04a-4eeb-83c5-940c63be77a4 /mnt/data1 ext4 defaults 0 0

```

Do the same for all your other partitions if you wish - then you can move your drives around or add new ones as you desire and everything will still boot/mount correctly.

---

### Post by Lappert on 2016-03-05
Weatherman2,

Thank you for your help and sorry for my delay in responding. Your explanation on mountpoints was helpful.

Your point about using UUID did help in assigning the drives. I was able to use the command lsblk instead of blkid to get the UUID numbers. 

Even with the UUID being specified in the fstab file, Ubuntu has a mind of its own, and puts whatever it wants as sdc. So even though the UUID was set to sdc, it still often ended up in folder /mnt/sdd. Don't know why or how that happened.

Nevertheless, fooling around with it long enough, I got it to stick to sdc.

Thanks again.

---

