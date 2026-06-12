---
title: "got a problem with mounting an ntfs partition...."
date: 2009-05-01
forum: Hardware
---

### Post by zero7404 on 2009-05-01
i configured my fstab file to be able to auto-mount my ntfs hdd upon startup each time, so that i have access to the directories in there....

however i recently wanted to try manually unmounting it (in a root terminal) so i used the umount command and it successfully unmounted....

but it won't auto-mount anymore when starting up ubuntu. i looked in fstab and the correct entry is there, also tried using the mount command but it doesn't work. looked in the file browser and when i click on the drive, it says i don't have privileges to mount it. looked at it's properties and everything listed under the basic tab is pretty much listed as "unknown"...

can anyone give some advice on what's going on, what i'm doing wrong ? just want it to go back to auto-mount upon ubuntu startup as before....

---

### Post by taurus on 2009-05-01
Which partition is your ntfs?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by zero7404 on 2009-05-01
> **taurus said:**
> Which partition is your ntfs?

```
sudo fdisk -l
cat /etc/fstab
```

here's the output from fdisk -l

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27c28482

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19582   157292383+   7  HPFS/NTFS
/dev/sda2           19583       38913   155276257+   5  Extended
/dev/sda5           19583       38791   154296261   83  Linux
/dev/sda6           38792       38913      979933+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd34d85db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568640+   7  HPFS/NTFS


here's the output from cat:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=084085b8-a429-4899-be94-d6090fc3bdb4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=5c012a54-1ef3-48fc-83b2-cab6045ddab6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/Storage ntfs-3g defaults,locale=en_US.utf8 0 0


---

### Post by taurus on 2009-05-01
I assume it's /dev/sdb1 since you have an entry in /etc/fstab for it.  What happens when you run this command from a terminal?

```
sudo mount -t ntfs-3g /dev/sdb1 /media/Storage
df -h
```

---

### Post by zero7404 on 2009-05-01
taurus, thanks for helping me out, i appreciate it....

how do i enter this in terminal, 

> sudo mount -t ntfs-3g /dev/sdb1 /media/Storage df -h

or 2 seperate entries ?

---

### Post by zero7404 on 2009-05-01
just tried...
```
sudo mount -t ntfs-3g /dev/sdb1 /media/Storage
```

the message i'm getting is...
> fuse: failed to access mountpoint /media/Storage: No such file or directory


---

### Post by taurus on 2009-05-01
Did you somehow manage to remove /media/Storage?  You need to create it again, running one line/command at a time.

```
sudo mkdir /media/Storage
sudo mount -t ntfs-3g /dev/sdb1 /media/Storage
df -h
```

---

### Post by drs305 on 2009-05-01
Zero,

The mount point has to exist. So create it with:
```
sudo mkdir /media/Storage
```

With NTFS partitions, the ownership is established at mounting rather than by who owns the actual mountpoint, but if you would like to be the owner of Storage, run this:
```

sudo chown -R *yourusername* /media/Storage # Example: sudo chown -R zero: /media/Storage

```

---

### Post by zero7404 on 2009-05-01
i'll try it out, i booted back into vista to make sure the drive is readable there (no problems found)....

i'll run these and see what happens, but i want to be sure i won't lose any data ?

---

### Post by zero7404 on 2009-05-01
thanks guys, these steps worked out flawless...

```
sudo mkdir /media/Storage
sudo mount -t ntfs-3g /dev/sdb1 /media/Storage
df -h
```

taurus, what is the difference between the df command and blkid ?

drs305, i assigned the mountpoint to my username in ubuntu, but is this a reversible process ? are there any side-effects to assigning the ntfs partition to my username ? lastly, if i chose to create a guest account in ubuntu, would the drive be prevented from mounting when the guest signs on ?

---

### Post by taurus on 2009-05-01
```

**blkid** - command-line utility to locate/print block device attributes

```

```
**df** - report file system disk space usage
```

---

### Post by drs305 on 2009-05-01
> **zero7404 said:**
> 
drs305, i assigned the mountpoint to my username in ubuntu, but is this a reversible process ? are there any side-effects to assigning the ntfs partition to my username ? lastly, if i chose to create a guest account in ubuntu, would the drive be prevented from mounting when the guest signs on ?

Assigning an owner is fully reversible. As far as side-effects, if you are the only user on the machine there really aren't any of great significance. 

If this was an ext2/3/4 partition and there were many of you on the computer, by running the command as I presented it you and your usergroup are the owners. This could block other users from accessing the folders unless they belong to your group as well. But the same would be true if the folders were owned by root.

In this case, NTFS partitions give read/write permissions to whoever mounted the device so who owns the partition before mounting isn't really a critical issue.

Here is the ubuntu wiki on Permissions:
[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by zero7404 on 2009-05-01
thanks again for everything, i greatly appreciate it and will give back to the community whenever i am able....

so how's 9.04 been working for you both, i noticed in your profiles you're running it....

i had a bad run with my first install, so i went back to 8.10 (clean install)....
i'm having trouble finding a good backup utility that will back up and restore entire ext3 partitions. i use acronis true image in windows and it works well, but it doesn't want to work well with ext3 partitions (must to sector-by-sector backup)....
do you know of anything out there that will yeild a good compressed image of my ext3 partition and swap partition ?

---

### Post by taurus on 2009-05-01
Maybe this is what you want, [http://www.clonezilla.org/](http://www.clonezilla.org/).

So far, Jaunty is running fine on my machines at home and in the office.

---

### Post by drs305 on 2009-05-01
> **zero7404 said:**
> do you know of anything out there that will yeild a good compressed image of my ext3 partition and swap partition ?

The ones I'll mention make copies of entire partitions - they aren't incremental backup answers. They are good for restoring a system that breaks or restoring an entire data partition. They are not for recovering single folders or files.

I've used partimage for years - it makes an exact copy of the partition except it doesn't copy empty space. 
[_How to Backup with Partimage_]("http://ubuntuforums.org/showthread.php?t=287522")
 
[_http://www.psychocats.net/ubuntu/partimage_]("http://www.psychocats.net/ubuntu/partimage")


Recently I moved to a simple command-line utility called fsarchiver because it can handle ext4 partitions, which partimage cannot as of now.
[_http://www.fsarchiver.org/QuickStart_]("http://www.fsarchiver.org/QuickStart")

Both offer a variety of compression levels.

---

### Post by zero7404 on 2009-05-01
i looked it over breifly once before, i will give it a shot, however i'm going to take my time reading thru the steps because i don't want to mess something up during the process of backup/restore...

will it work well with a multi-partition hdd ? for example, i have grub installed, then vista, then ubuntu and lastly my swap area....

if i could use clonezilla to image the entire disk, that would be best. also, i'm going to want to be able to save the image on the ntfs drive...if this is not possible, i could split that partition to make another one that is readable by clonezilla....

---

