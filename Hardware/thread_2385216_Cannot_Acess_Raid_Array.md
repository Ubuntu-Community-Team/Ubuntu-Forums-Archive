---
title: "Cannot Acess Raid Array"
date: 2018-02-17
forum: Hardware
---

### Post by indgepr on 2018-02-17
I have just installed lubuntu 17.1 over the top of Ubuntu 16.04

The computor has 3 Disks 
sda - single drive
sdb &sdc - Raid 1

in Ubuntu these were mounted to /media/data but I cannot get it to work

I have tried

sudo mdadm --assemble --verbose /dev/md0 /dev/sdb /dev/sdc

This gives

mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb is busy - skipping
mdadm: /dev/sdc is busy - skipping

If I try 

sudo mount /dev/sdc /media/data
mount: /media/data: unknown filesystem type 'linux_raid_member'.

Please help as all my music etc is on the drives

---

### Post by SeijiSensei on 2018-02-18
Are you sure you should be mapping the entire devices rather than the partitions they contain?  

Since the filesystems are marked as RAID members, you might just let mdadm figure out how to build the array itself.  What about just
```
sudo mdadm --assemble /dev/md0
```

If that doesn't work, have you tried joining the partitions on the devices rather than the devices themselves?
```
sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
```

---

### Post by indgepr on 2018-02-18
Thanks for the suggestion unfortunately neither helped. the output is as follows

```
$ sudo mdadm --assemble /dev/md0
mdadm: /dev/md0 not identified in config file.
```

```
sudo mdadm --assemble /dev/md0 /dev/dbd1 /dev/sdc1
mdadm: cannot open device /dev/dbd1: No such file or directory
mdadm: /dev/dbd1 has no superblock - assembly aborted
```

In the dev folder there are the following entries along with alot of others that I dont thing are involved in this case
Folder - md containing File ProLiant-MicroServer:0
Files sda , sda1 , sda2 , sda5 , sdb , sdc 

No sdb1 etc 

Hope this helps

Phil

---

### Post by SeijiSensei on 2018-02-18
You typed "/dev/dbd1" instead of "/dev/sdb1".  Did that not work either?

What if you run "sudo fdisk /dev/sdb" and "sudo fdisk /dev/sdc"? Do the devices have partitions? What are their types (e.g., "Linux", "Linux RAID", etc.)?

I have a RAID-1.  The two devices each have a single partition (e.g, /dev/sdd1) of type "Linux RAID" that spans the entire drive. Those partitions are joined to make my array.

You could also try as an emergency method, mounting one half of the array as a normal filesystem.  This has worked for me with RAID-1 and an ext4 filesystem on the array. When you tried that before you had a file type problem.  Try mounting /dev/sdc1 to /media/data.  Any better?

---

### Post by indgepr on 2018-02-20
Still no success.
```

sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdc
mdadm: /dev/sdb is busy - skipping
mdadm: /dev/sdc is busy - skipping

```

```
sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
mdadm: cannot open device /dev/sdb1: No such file or directory
mdadm: /dev/sdb1 has no superblock - assembly aborted
```

In the /dev/md folder there is a file that is a shorcut to md127 in the /dev folder so I tried
```

sudo mount md127 /media/data
mount: /media/data: wrong fs type, bad option, bad superblock on /dev/md127, missing codepage or helper program, or other error..
```

and with your sugestion

```
indgepr@ProLiant-MicroServer:/dev$ sudo mount sdc /media/data
mount: /media/data: unknown filesystem type 'linux_raid_member'
```

running the fdisk command gave

```
sudo fdisk /dev/sdb
Welcome to fdisk (util-linux 2.30.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

The old linux_raid_member signature will be removed by a write command.

Device does not contain a recognised partition table.
Created a new DOS disklabel with disk identifier 0x1043d599.

```

Also get the following

```
dev$ sudo mount /md/Proliant-MicroServer:0 /media/data
mount: /media/data: bad option; for several filesystems (e.g. nfs, cifs) you might need a /sbin/mount.<type> helper program.

```

I think it is a ext2 file system on the drives from 

```
fsck -N /dev/md/ProLiant-MicroServer:0 
fsck from util-linux 2.30.1
[/sbin/fsck.ext2 (1) -- /dev/md127] fsck.ext2 /dev/md127 

```

---

### Post by indgepr on 2018-02-24
having read elsewhere I have installed the nfs-common and nfs-kernal-server. started the nfs kernal server.

Now when I try to mount the /md/Proliant-MicroServer:0 get the error 

mount.nfs4: Connection timed out


Any one got any ideas ?

---

