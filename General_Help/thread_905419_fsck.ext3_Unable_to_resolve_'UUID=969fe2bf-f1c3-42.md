---
title: "fsck.ext3: Unable to resolve 'UUID=969fe2bf-f1c3-42a1-b658-23a6d3d00d22'"
date: 2008-08-30
forum: General Help
---

### Post by asenine on 2008-08-30
Hey guys,

This UUID belongs to sda1. What do I do to stop this error from occuring? People on IRC told me to do 'sudo blkid', but that did nothing.

Any ideas?

Also, if I want to run fsck in non-automatic fixing mode, do I just do fsck --r, or what?

Thanks!

- Chris

---

### Post by NewDisciple on 2008-08-30
Post the entire output of > cat /etc/fstab

---

### Post by Zorael on 2008-08-30
I may be completely misdiagnosing this, but here goes. Open your /etc/fstab file in a text editor and compare the entries with the output from sudo blkid. Do the UUIDs differ?

For instance, this is the definition of my root partition in said file.
```
# Entry for /dev/sda3 :
UUID=e900fd0f-a313-41d1-8e26-796933c430a4 / ext3 noatime,data=writeback,errors=remount-ro 0 1
```
If the UUID there differs from the partition's "real" UUID (blkid output), things will go bad. You could either replace that section with the real one, or just replace it with the device node for that partition (dev/sd**). This would translate to the following.
```
# Entry for /dev/sda3 :
**/dev/sda3** / ext3 noatime,data=writeback,errors=remount-ro 0 1
```
As always, make a backup of that file before making any changes, and make sure you have a live cd or equavilent if you botch stuff up, to be able to revert your changes.

If you have several harddrives and your controller card/chipset insists on changing the device nodes (which one is sda and which is sdb, for instance), you're better off using the UUIDs, but in the vast majority of cases that's not the case. case case case.

---

### Post by retrovertigo on 2008-08-30
An alternate way of verifying the UUID is to run the command **ls -l /dev/disk/by-uuid**.

Always helps to know more than one way of finding information!

---

### Post by drs305 on 2008-08-30
Zoreal gave you the instructions but if you are unclear, in addition to the "cat /etc/fstab" post the results of "sudo blkid" and we can straighten out your fstab.

Also, do not run fsck on a normally-mounted partition. If it's one of your system partitions (/ or /home if you have one) do it from the recovery mode or LiveCD.

---

### Post by NewDisciple on 2008-08-30
Emphasis on blkid output - real name.  Are you not wanting fsck to run automatically?  If so that info is in the forums.   "sudo fsck -p" is used to auto-repair ext.3 file systems.  I believe the partion has to be unmounted first.  Easier to "sudo touch /forcefsck" shut down & restart I suppose.  Just musing.

---

### Post by Scunge on 2008-08-30
> **asenine said:**
> Hey guys,

This UUID belongs to sda1. What do I do to stop this error from occuring? People on IRC told me to do 'sudo blkid', but that did nothing.

Any ideas?
I'd like to add that I get this error too, during bootup, for external USB disks. I specifically want to use UUIDs because otherwise the two disks can sometimes end up being mounted in the other order and links to them no longer work.

My output, to show I have the correct UUIDs is:

```
$ sudo blkid
[...]
/dev/sda5: UUID="b7094347-fe9c-4fc6-aaac-a2f1758377cd" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="3f7716a9-7bd5-479a-80c2-8ddb7fa8824c" SEC_TYPE="ext2" TYPE="ext3"

$ cat etc/fstab
[...]
UUID=b7094347-fe9c-4fc6-aaac-a2f1758377cd /media/Storage ext3 rw,nosuid,nodev 0 0
UUID=3f7716a9-7bd5-479a-80c2-8ddb7fa8824c /media/Others ext3 rw,nosuid,nodev 0 0

$ ls -l /media
[...]
drwxr-xr-x 2 root root 4096 2008-08-30 10:43 Others
drwxr-xr-x 2 root root 4096 2007-06-18 10:13 Storage

```

Perhaps these problems are related?

> **asenine said:**
> Also, if I want to run fsck in non-automatic fixing mode, do I just do fsck --r, or what?

It does depend exactly what partition you are wanting to check, and when.

The "-f" option force checks a partition even if it appears clean. So you probably want that.

The "-p" option says that automatic repairs can be used, if simple to repair. So you **don't** want that if, as you say, you "want to run fsck in non-automatic fixing mode".

The "-v" option means "verbose", which is useful. So I'd say you should use that.

The "-c" option does a bad blocks check as well as the other stuff it does anyway, so I guess you want that.

If you really want to give the partition a thorough check, another "-c" option does a "non-destructive read-write" check. Will take alot longer, but may be worth it.

The "-k" option keeps any existing bad blocks to be still marked as bad, which I think is a good idea in case intermittent disk failures. So I'd say you should use that.

So if it were me in your situation, I'd use
```
fsck -cckfv /dev/sdax
```
or, at a minimum,
```
fsck -fv /dev/sdax
```
with "sudo" on the front if done from a running system and not the Live CD.

---

### Post by rogerhc on 2008-09-26
> **asenine said:**
> 
Hey guys,
This UUID belongs to sda1. What do I do to stop this error from occuring? People on IRC told me to do 'sudo blkid', but that did nothing.


I think I'm having the same problem and that it is NOT sda1's UUID failing to resolve -- every time I boot Ubuntu Hardy Heron (on sda7) fsck looks at sda1, then can't resolve some UUID, sticks and tells me I can press Ctrl+D to continue booting. Fsck also kindly reminds me that it has logged this in /var/log/fsck/checkfs, which shows the following:

```

roger@spray:~$ cat /var/log/fsck/checkfs 
Log of fsck -C -R -A -a 
Fri Sep 26 08:53:01 2008

fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 51271 files, 1077185/1279219 clusters
fsck.ext3: Unable to resolve 'UUID=8c569fef-7ad6-4872-91a3-6bd3fb0a4c33'
fsck died with exit status 8

Fri Sep 26 08:53:38 2008
----------------

```

Please note: there is no relationship between above "/dev/sda1..." line and the one below it unable to resolve UUID 8c569fef-7ad6-4872-91a3-6bd3fb0a4c33. Don't confuse those two lines to be discussing the same partition. Fstab, below, shows UUID 8c569fef-7ad6-4872-91a3-6bd3fb0a4c33 for sda6. Fsck is simply trying to check filesystems in the order listed in /etc/fstab and sticking on the sda6  entry because the UUID listed for sda6 there wont resolve. It can't because (I think) I changed the sda6 partition somehow when I installed another distro there recently such that sda6 now has a new UUID, as you can see in the blkid listing that follows fstab, below. Fstab however, traditionally only edited by the sysadmin (that's me and you) was not duly updated because you and I forgot to update it.

```

roger@spray:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=10bee5ca-e0cc-4d35-a521-a669a02b2d08 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7844-F80A  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=8c569fef-7ad6-4872-91a3-6bd3fb0a4c33 /media/sda6     ext3    defaults        0       2
# /dev/sda5
UUID=343b2ef8-0294-4fb7-abaa-fbe6f67b9bc8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
roger@spray:~$ 

```

```

roger@spray:~$ sudo blkid
/dev/sda5: TYPE="swap" UUID="343b2ef8-0294-4fb7-abaa-fbe6f67b9bc8" 
/dev/sda6: UUID="4b466bc5-84af-45fc-b9e5-6c3074fe72e1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="10bee5ca-e0cc-4d35-a521-a669a02b2d08" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: LABEL="M-^IPNG^M^J^Z^J" UUID="7844-F80A" TYPE="vfat" 
roger@spray:~$ 

```

I will now edit the sda6 UUID listed in /etc/fstab to the UUID listed in blkid. Hope this works :-) ...

---

### Post by rogerhc on 2008-09-26
Huray! That fixed it for me. No more stalling at bootup.

---

