---
title: "ubuntu 14.04 LTS mount and change ownership of internal HD"
date: 2016-01-23
forum: Hardware
---

### Post by Callmestupid on 2016-01-23
This is what I have done so far errored out and still haven't changed fstab yet.
```

randell@randell-MS-7390:~$ sudo parted -l
[sudo] password for randell: 
Model: DMI External HDD (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  616GB   616GB   primary   ext4
 2      616GB   1000GB  384GB   extended
 5      616GB   992GB   375GB   logical   ext4            boot
 6      992GB   1000GB  8588MB  logical   linux-swap(v1)


Model: Toshiba External USB 3.0 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 4096B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB
 2      2097kB  2992GB  2992GB
 3      2992GB  3001GB  8589MB


Model: ATA Hitachi HDT72101 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  992GB   992GB   primary   ext4            boot
 2      992GB   1000GB  8588MB  extended
 5      992GB   1000GB  8588MB  logical   linux-swap(v1)


Model: ATA Hitachi HDT72101 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  992GB   992GB   primary   ext3
 2      992GB   1000GB  8588MB  extended
 5      992GB   1000GB  8588MB  logical   linux-swap(v1)


Model: ATA ST3120213AS (scsi)
Disk /dev/sde: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  114GB  114GB   primary  ntfs         boot
 2      114GB   120GB  6185MB  primary  ntfs

```
```

randell@randell-MS-7390:~$ sudo blkid
/dev/sda1: LABEL="Spare" UUID="3c90f083-668c-40be-afea-5083779b73db" TYPE="ext4" 
/dev/sda5: LABEL="Mythbuntu" UUID="5cc811de-ca89-44ed-a6f7-0f1429c7a49a" TYPE="ext4" 
/dev/sda6: UUID="67f5991d-bbea-455d-8b1a-d55bc6faabf5" TYPE="swap" 
/dev/sdb2: LABEL="Christian Music" UUID="7420AA793341732B" TYPE="ntfs" 
/dev/sdb3: UUID="485a9bed-9eb3-445f-b556-d0e33fc835ce" TYPE="swap" 
/dev/sdc1: LABEL="Data01" UUID="6facc9ee-f062-4070-984e-c7ae53c53844" TYPE="ext4" 
/dev/sdc5: UUID="3c9c48f2-fad5-4b38-92d7-bca40ef40180" TYPE="swap" 
/dev/sdd1: LABEL="Disk02" UUID="05df5337-9bf1-4ac6-a4b7-a1cc94de2107" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd5: UUID="b1349234-68f9-48d0-931a-80b79516b443" TYPE="swap" 
/dev/sde1: UUID="CA5C671C5C670315" TYPE="ntfs" 
/dev/sde2: LABEL="Recovery" UUID="2C88743C8874071C" TYPE="ntfs" 

```
```

randell@randell-MS-7390:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=6facc9ee-f062-4070-984e-c7ae53c53844 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3c9c48f2-fad5-4b38-92d7-bca40ef40180 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=82db6f04-4e89-4b018ae7-b01f988f9625 /                ext3
/dev/disk/by-uuid/CA5C671C5C670315 /mnt/CA5C671C5C670315 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/05df5337-9bf1-4ac6-a4b7-a1cc94de2107 /home/data/\040dev/disk02 auto nosuid,nodev,nofail,x-gvfs-show 0 0

```
Did the following:
```

randell@randell-MS-7390:~$ sudo mount /dev/sdd1 /mnt/data
randell@randell-MS-7390:~$ sudo chmod -R a+rwX,o-w /mnt/data
randell@randell-MS-7390:~$ sudo chown -R randell:randell /mnt/data

```
got the following error msg:

Unable to acess “disk02”

mount: according to mtab, /dev/sdd1 is mounted on /mnt/data
mount failed


according to Disks the disk is mounted, 

device reads: /dev/sdd1
parician type reads: Linux
contents reads: Ext3 (version 1.0) — Mounted at /mnt/data

I can not access the disk.

I was following instructions in the following Ubuntu forums thread:
[http://ubuntuforums.org/showthread.php?t=1840948](http://ubuntuforums.org/showthread.php?t=1840948)

JohnPta 

"Some people say if you play a windows cd backwards it plays satanic messages. That's nothing, because if you play it forwards it installs windows!" (Author unknown)

That's funny all the windows in my house are still the ones that were here when I moved in!!! And I still need new replacement windows!!!

---

### Post by TheFu on 2016-01-24
Please edit the post above and use "code tags" so the output lines up. Too hard to read as is.
See my signature for "code tags" how-to.

Assumptions:
* a partition exist on the new disk already.
* a file system exists on the new partition inside the disk already.
* device names are already known. Use sudo blkid or check dmesg to see device names.
* if permanent mount is desired, then the fstab must be edited. It is **best** to use UUIDs inside the fstab.  Device names can change, UUIDs do not.
* For temporary mounts, /mnt/some_dir is best.
* For permanent mounts, /create/a/directory outside /media and /var unless you have a specific reason to use directories under there.  An example is that /var/www holds web files, so adding storage to /var/www is a valid reason.  Similarly, /var/lib/libvirt/ is where virtual machine vHDDs are placed, so adding a few TB there could be useful.  For media files that are going to be permanently mounted, I avoid /media/xyz - that location is managed by the OS and if there is a bug and a conflict happens, well, it may not be a good day for your files. Just sayin'.

Steps:
1) Create a mount-point for a new partition. This is **not** usually the entire disk, but a partition.  A mount-point is simply an empty directory. Best to avoid funny characters or spaces when beginning.  Sudo may be needed. This is strictly based on normal file/directory permissions for the parent directory of the new created location. It has ZERO to do with mounting.
```
mkdir /full/path/to_dir
``` 
 OR 
```
mkdir -p some/relative/path

```
2) Mount the device to that new directory. sudo must be used for mount - it is actually a very dangerous command and any userid allowed to "mount" can completely take over a system.
```
sudo mount /dev/sdZ99  /full/path/to_dir
``` 

3) Check that the permissions are set as desired. This only works for Linux-based file systems, not NTFS or FAT-whatever.  Permissions for those can only be changed at mount time.
```
ls -al /full/path/to_dir
``` 
If the mount type is ext4/3/2, jfs, btrfs, zfs, etc ... and the permissions/owner aren't correct, use the **sudo chown -R ** to correct the owner, then use **chmod -R** as your useid to fix any permissions.  I assume you will check the manpages for specific options to chown or chmod as needed. **NEVER RUN A COMMAND WITHOUT UNDERSTANDING EACH OPTION.** Ubuntu has a **Linux Permissions Tutorial** that isn't bad - not great, just not bad. Web search will find it.  Linux is a multi-user OS from the ground up and file + directory permissions are the cornerstone to system security.  Best to learn and understand these as early in your Linux life as possible.  I put it off longer than I should have and I regret that.

There is no chown/chmod command that can alter the permissions for NTFS or FAT16/32/xfat file systems. None, zero, nada. For those, the permissions **must** be selected at mount time through mount options - uid, gid and a few others like dmask and fmask. I always have to check the manpage myself.

4) Once permissions and ownership is set on a Linux file system or mounted file system, it shouldn't change unless some one else manually changes it. If it changes after a reboot, then there are multiple mount systems screwing around.  If you always use the shell commands or fstab, then you'll never have nautilus fighting with you about mount ownership.

Instructions that say to run any GUI program as root can cause bad things to happen because GUI programs tend to write config settings to places based on $HOME.  gedit does this and I've seen systems become extremely difficult because someone ran *sudo gedit* just after an installation was performed. Bad idea. Use **sudoedit path/to/file** to edit any system settings. This is always safe, which is a good thing.

</soapbox>

There are many tutorials for fstab mounting. Basically, copy the line already in the file that looks like the correct file system, then swap in your mount-point and UUID.  Of course, use **sudoedit /etc/fstab** to do the editing. ;)  After you finish, run **sudo mount -a** - no other options needed. This will read the fstab and mount anything that isn't already mounted.

6) To see which file systems are mounted, use either 
```
**df -h**
```
or
```
**mount**
```

I find the df cmd to be easier to read. The only reason I use the mount command is if I need to see the specific options used.  The **man fstab** manpage isn't bad, if you need more details.

If you want to up your mounting and storage management game, it is very common to use LVM2 to have 100x more flexibility in the storage use.  LVM is amazing, but can be ignored for most beginners and end-users.  OTOH, if you need advanced storage capabilities, like growing or shrinking a file system while it is being used, then LVM can do that in many situations.  It is also great for backups, since you can create a static "snapshop" of a running system and backup the snapshot to slower storage while the system continues running.  This is very cool if you have a DBMS that cannot be shutdown.  LVM has multiple ways to group storage together - physical, volume groups and logical volumes.  Logical volumes can be thought of as a partition that can be resized, mirrored, moved, shrunk all while remaining online (while the system it running). LVs are mounted like partitions. They have something like a UUID, but it is a mapper file which doesn't change between boots.  Very cool. Very powerful.  And we haven't mentioned encryption at this point.  LVM can make whole disk encryption much easier to use.  Anyway - I use LVM on all physical drives - it is that powerful to be worth the slight extra complexity.

Anyway - hope this helps - less with commands and more with "why."

---

### Post by Callmestupid on 2016-01-25
OK, I still have the same problem sdd1 is mounted but not usable. df -h results follow:
```

df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           799M  1.2M  798M   1% /run
/dev/sdc1       909G  410G  453G  48% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            3.9G   80K  3.9G   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sde1       107G   97G  9.5G  92% /mnt/CA5C671C5C670315
/dev/sda5       344G  3.1G  324G   1% /media/randell/Mythbuntu
/dev/sda1       565G  209G  328G  39% /media/randell/Spare
/dev/sdb2       2.8T  1.7T  1.1T  61% /media/randell/Christian Music
/dev/sdd1       909G   72M  863G   1% /mnt/data

```

on my files screen is showes disk02 but there is no mount arrow to the right side of this device.

I think I have part of it figured out that it is mounted in /, where I think I should have in mounted in my /home/randell/data? 

At present it is mounted in /mnt/data

I want it to be easy to get to. At present I discovered I can make folders etc only if I go to /mnt/data where it is mounted. I'm sorry if I'm not making a lot of sence, I think I'm getting too confused with all this. If that is what I need to do how do I unmout that partition to change the mount point?  I have not changed the fstab file yet as I was not able to figure out how to create new files and folders on that drive unitl a couple of minutes ago. I probably will try the LVM2 once I have this figured out unless it might be easier if I get that first. Sometimes think I'm getting too old, seem to get confused easier.

---

### Post by weatherman2 on 2016-01-25
If you want to change ownership of the partition on /dev/sdd1 - currently mounted at /mnt/data - then do this:

```

sudo chown -R randell:randell /mnt/data/

```

You can mount it wherever you wish  - /mnt/data or /home/randell/data if you like that better.

---

### Post by Callmestupid on 2016-01-25
This is where I am at present:

```

[mntent]: line 15 in /etc/fstab is bad

```

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=6facc9ee-f062-4070-984e-c7ae53c53844 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3c9c48f2-fad5-4b38-92d7-bca40ef40180 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=82db6f04-4e89-4b018ae7-b01f988f9625 /                ext3
/dev/disk/by-uuid/CA5C671C5C670315 /mnt/CA5C671C5C670315 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/05df5337-9bf1-4ac6-a4b7-a1cc94de2107 /home/randell/data/ ext 3  auto nosuid,nodev,nofail,x-gvfs-show 0 0

```

---

### Post by Dennis N on 2016-01-25
> I want it to be easy to get to. At present I discovered I can make folders etc only if I go to /mnt/data where it is mounted.

File systems mounted in fstab don't appear automatically in the file manager's side pane. You just need to make a book mark for them instead. It could be for any folder in your sdd1 file system, but start with the mount point itself - you can make more bookmarks later.

In the attached screen shot of the side pane, the bookmark (shows under Places) for "Common-Files" is actually the top folder (mount point) of my data partition's file system, making it easy to access without browsing to where it is mounted.
.......................
Also, your last two fstab lines look a bit weird to me. Do they work? I mount my data partition file system with this (first line is an optional comment), for example:

```
# Label=Common-Files /dev/sda4
UUID=d97e2feb-1bf6-429b-bba5-943264ec1474 /mnt/Common-Files ext4 defaults 0 2

```

---

### Post by TheFu on 2016-01-26
fstab mounts are "system mounts" - these are different from those created using a GUI/file manager.  File manager mount use gvfs which has some limitations that I've elected to never learn about and never use.  The main limit is they are placed in single-user-accessable directories. In my mind, either storage is mounted to the computer for all users or it isn't.  Don't forget that each service runs as a different userid, so this doesn't relate to 1 human. Linux is a multi-user system from the start, so be certain your choices work for that, if you care.

There are many, many how-tos for the fstab, so I won't repeat them. The ones I'd point to all have "ubuntu" in the domainname.  help.ubuntu.com or askubuntu.com are reputable.  For the last 3 LTS releases, gvfs has changed where end-user mounts are connected.  Under /media and sometimes under /var and sometimes with a userid or not.  They are trying to solve security issues, that just don't exist if people used system mounts through either the fstab or autofs (that's something for a different day).  The real secret to fstab lines is to copy/paste the data. Don't type it.

So - I know you didn't ask, but my recommendations are:
a) Don't use file managers to mount storage for long-term use. gvfs has a use, for someone. Just not me for many reasons. 
b) Always use the /etc/fstab or autofs to create "system mounts" (that is my term, not something others use)
c) Almost always mount long-term storage outside /var and /mnt and /media directories. I would avoid under /home too. /home directories really should avoid having lots of data, since that makes backups slightly harder to manage.  By keeping large data outside /home, you are more likely to easily backup /home which can save your settings and other important files.  These are opinions, so others may have a different take. /mnt is for temporary system storage. /media is for extremely temporary storage - I think USB drives with foreign file systems like NTFS/xFAT ... stuff like that.

Where should you mount permanent storage? Well, that depends.  For large media files, I put stuff under /D/ ... so /D/M, /D/T, /D/Music, /D/HomeVid ... you get the idea.  Then I use NFS to share that storage to other authenticated devices on the network so they all get access based on normal, standard, Unix file and directory permissions.  NFS storage behaves like local, permanent, storage in about 99.999999999% of the ways we need.

Why not use a GUI? I mostly work on servers, so there isn't any GUI, so it isn't possible/desired. The fstab or autofs methods work on servers exactly the same as they do on desktops. Learn one thing and it works. That saves time, effort in the long run.  There have been slight changes to the fstab file over the years, but it is basically the same as it was in 1991. File managers seem to be re-written every 3 years and the underlying gvfs stuff seems to change biannually. Gvfs mounts don't act like normal mounts and if you don't always use gvfs-aware GUI tools, that storage won't show up. I find that truly offensive, to put it nicely. A mount should be a mount!  Windows does this with their "Libraries" - libraries aren't file system objects, so they don't work inside cmd.exe at all. That means they are useless to me and not worth my time. The same applies to gvfs mounts. Not worth my time, because they don't show up everywhere a normal mount does.  Whenever I ssh into a box or sftp in to grab a file from overseas, I don't want to wonder ... did I mount that with gfvs and that's why it doesn't show up now?

I do see where end-users would love gvfs, I really do, but they don't always understand the limitations of a tool. If it isn't important, fine. For me and my users, those limitations matter.

Life has too many unnecessary exceptions. I find it easier to avoid those whenever possible. I'm simple that way. OTOH, my storage "just works" too.

</soapbox>
Sorry about that.

Your fstab file in #5 above is incorrect.  
* You cannot mount 2 partitions to / - THAT IS A HUGE, BOOT SCREW-UP MISTAKE. Fix ASAP!
* /dev/sdX9 is a device or UUID=xxxxxxxxxxxxxxxxxxxxxxxxxxx is the format for the 1st field. Don't mix those on a single line. There is a proper UUID example already in the file. Follow it. 
* gvfs has no place in the fstab. Where'd all those options come from?
* I've learned that mounting storage under a /home is a bad idea for most uses. You can do it, but you've been warned. Mounts that depend on 2 other mounts existing are a bad idea. What happens if /home doesn't get mounted? Today, you don't have a separate /home mount ... maybe you should since that is where you are trying to mount data?

Anyway, if you are truly stuck, point which disks you want where and the fstab can be provided. I see you've been trying to learn - not just "give me the answer" - which I'm happy to help others learn this stuff based on almost 25 yrs of experience.

---

