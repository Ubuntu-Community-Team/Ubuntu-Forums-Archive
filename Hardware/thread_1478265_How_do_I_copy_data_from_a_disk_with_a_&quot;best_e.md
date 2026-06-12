---
title: "How do I copy data from a disk with a &quot;best effort&quot;"
date: 2010-05-09
forum: Hardware
---

### Post by fishtoprecords on 2010-05-09
I've got a nice new 1.5tb SATA disk, and a bunch of really old 60GB and 80GB IDE disks. I want to transfer the data from the old to the new.

There seem to be some problems in the old disks,  so a simple
 "cp -r" fails. As does the GUI equivalent.

I can live with only getting 95% of the data, or whatever amount is readable. But I can't figure out how to copy the data. I want something that will copy the data if possible, and if not, fail quietly and go on to the next file.

Thanks

---

### Post by r-senior on 2010-05-09
Have you tried using find?

Something along the lines of:

$ cd /mnt/baddisk
$ find -exec cp -a {} /mnt/gooddisk/ \;

I'm not sure whether find will carry on when you hit a bad file, but worth a try. The executed command (cp) should be run once for each file.

---

### Post by Quo on 2010-05-09
First: don't access the flaky disks read-write. (It sounds like you already may have). If you absolutely have to mount them (and you don't), mount them read only, to avoid messing up a superblock that may not be reliably writable.

[LIST=1]
[*]salvage each partition as a disk image
[*]store an unmodified copy of that image somewhere safe
[*]fsck a copy of the disk image
[*]mount the disk image
[*]check your files - they're readable without trouble now, but some may be missing or be truncated
[/LIST]

Fetch a disk that's large enough to hold *images* of the disks you want to salvage. Then use dd (I recommend sdd, from Joerg Schilling for that task), to fetch the blocks from the disk. 

sdd  if=<raw device of your defective partition> of=<new file on disk with enough space> bs=<should match your blocksize> conv=sync, noerror

The important part is the last one: conv=sync tells dd to pad all those blocks it could read only partially with zeroes, so the resulting image may have a few zeroes too many, but will structurally equal the flaky disk, minus its read errors. For plain dd, the syntax remains the same.

**Important**: If a block cannot be read, it will be re-tried (and the disk also will try to repair/remap it). Due to this, it can take a long time to read an entire disk. Make sure your setup is left to run uninterrupted during that time. 

(On a 60GB notebook disk that had been badly damaged, it took dd *two entire weeks* to scratch all it could read from the erroneous disk.  Watch out for your /var partition - the error logs from all those read attempts can flood it. If necessary, turn off logging them, or empty the logfiles before they're suffocating you.  ((Don't remove them - they're not gone as long as they're kept open. Truncate them using :> *filename* instead, for example.

Once you're done, take a copy of that image, fsck it, and mount it to see what's left of your filesystem.

---

### Post by fishtoprecords on 2010-05-09
> **Quo said:**
> First: don't access the flaky disks read-write. (It sounds like you already may have)

You are correct, I didn't think to mount it RO.
And it does take forever.....

I'll try your ideas.

---

### Post by fishtoprecords on 2010-05-09
> **Quo said:**
>  bs=<should match your blocksize>

How do I find the blocksize of the existing disk/partition?

---

### Post by fishtoprecords on 2010-05-09
> **Quo said:**
> sdd  if=<raw device of your defective partition> of=<new file on disk with enough space> bs=<should match your blocksize> conv=sync, noerror


when I try this, using
sdd -version
sdd 1.52 (i686-pc-linux-gnu)


I get an error:

sdd if=/dev/hdh1 of=/bay5/imagebay1 bs=4096 conv=sync noerror
sdd: Bad Option: 'conv=sync'
Usage:	sdd [option=value] [-flag]

This happens both with and without the command after "sync"

---

