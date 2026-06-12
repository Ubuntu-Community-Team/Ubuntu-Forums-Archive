---
title: "fsck on LUKS LVM on RAID5 erroring out on run, out of memory error"
date: 2015-05-04
forum: Hardware
---

### Post by tylersontag on 2015-05-04
I've got an ext4 LUKS LVM running on a RAID5 setup with 3 2TB drives and i had a failure occur the other week.

After having the RAID not assemble properly i brought it up using --force and got a message about one of the drives updating their event counter.

When i unlocked and mounted the drive, i noticed some folders missing from the drive, those that were there had some files missing, I/O error inaccessible, or folders showing up as files.

Right now, i'm trying to run fsck on it, to hopefully salvage as much as i can off of it before i move it to a new RAID (think this event and the drives age are a good sign that greener pastures are called for) but i'm having trouble running the check

```
xxx@yyyy:~$ sudo fsck -V -y -C /dev/mapper/luks-ddbcd457-cbeb-442f-b720-8f0383c86a6a 
fsck from util-linux 2.20.1
[/sbin/fsck.ext4 (1) -- /dev/mapper/luks-ddbcd457-cbeb-442f-b720-8f0383c86a6a] fsck.ext4 -y -C0 /dev/mapper/luks-ddbcd457-cbeb-442f-b720-8f0383c86a6a 
e2fsck 1.42.9 (4-Feb-2014)
TagRAID was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks

...
```

It gets through Pass 1: but on Pass 1B: it starts spitting out thousands of numbers and memory usage gradually increases until 92% of my 4GBs of RAM are used and the process will crash saying that it was unable to allocate xx bytes for inode.

I've setup an e2fsck.conf file and defined a [scratch_directory] which seems to be being used, but i'm still getting this issue.

I've dismantled a partition i didn't need and added an extra 10GB of swap space, but it doesn't seem to be using it.

Any thoughts on some things to try?

---

### Post by tylersontag on 2015-05-04
Still getting an error, in roughly the same place.

I've ran e2fsck directly, passing -p, hoping that perhaps each run its able to get a little more and a little more done, but I don't think that's happening :-/

---

