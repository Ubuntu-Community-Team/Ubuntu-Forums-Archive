---
title: "Mounting broken LVM ext4"
date: 2019-09-03
forum: Hardware
---

### Post by krupers92 on 2019-09-03
Hi!
Two years ago I created LVM which consists of several HDDs with total capacity about 30TB. Recently I've realized that two HDDs starts failing so I migrated both volumes into one new (bigger) HDD with lvmove and removed old disk from VG with lvreduce. After reboot I am unable to mount my root partition.

```
root@ubuntu:/home/ubuntu# mount /dev/mapper/HP--BACKUP--vg-root /mnt/test
mount: /mnt/test: mount(2) system call failed: Structure needs cleaning.
```

of course I've tried fsck:
```

ext2fs_check_desc: Corrupt group descriptor: bad block for block bitmap
fsck.ext4: Group descriptors look bad... trying backup blocks...
/dev/mapper/HP--BACKUP--vg-root: recovering journal
fsck.ext4: unable to set superblock flags on /dev/mapper/HP--BACKUP--vg-root


/dev/mapper/HP--BACKUP--vg-root: ***** FILE SYSTEM WAS MODIFIED *****

/dev/mapper/HP--BACKUP--vg-root: ********** WARNING: Filesystem still has errors **********
```

Because of quite big volume size I'm unable to dd into another disk for tests. Right now I don't need a bootable system - "just" recover some files. Do you have any ideas how could I possibly access my files?

---

### Post by TheFu on 2019-09-05
Waited a few days before replying, hoping someone else would have some ideas to help.  

Resizing the underlying partition doesn't resize the file system.  Did you do that too?   **lvresize** has an option to resize the filesystem when the LV is resized. **resize2fs** for after-the-fact attempts.  I've used lvreseize to reduce AND increase an LV and file system many times.  I don't fully allocate all the storage in a VG.

Seeing the exact commands used, in the exact order, with all the exact options might help someone to help you.

Sometimes we can mount corrupt file systems read-only.  Tried that?

The last idea is to try some things in the "ubuntu data recovery" guide.  Google for it.  This will be painful.

For the future.
Storage setup needs to be about what you can and need to backup.  Backups cannot be replaced. Not ever.  If you can't backup to a simple storage solution, then the storage design is wrong.  My solution is to limit all storage allocation to 4TB or less. This is because my backup disks are not larger than 4TB at this point.  I use LVM, like you, but still limit any LVs to 4TB.  BTW, I have about 40TB of storage total, but about 18G is for backup needs.  Things that need to be backed up are specifically placed based on the type of data contained and the sort of backup used.

I use a backup tool with versioning for OS settings, personal settings, documents, "server" and DBMS data. Generally, these backups have between 60 and 180 days of versions.
For media files, I use a relatively simple rsync mirror solution for practical reasons.  I'm nearly out of storage for media and going through to delete old time-shifted recordings that have just always been around that nobody has or will watch.

You could work around the simple backup requirement by using very selective pattern matching on the huge source, but the target backup storage needs to be sized such that as a stand-alone device, it can easily access all the files there from almost any live-boot Linux environment.  Permissions, owner, group, ACLs AND the data all need to be captured (for any lurkers).  The data alone is not sufficient.

Lastly, dd has a modern replacement - **ddrescue**.  ddrescue does what dd does, but it will keep going when there is a small problem. Plus ddrescue will continue trying after it skips the problem areas.   dd will stop.

Good luck. Sorry I don't have any better ideas.

---

### Post by slickymaster on 2019-09-05
Thread moved to **Hardware** for a better fit

---

