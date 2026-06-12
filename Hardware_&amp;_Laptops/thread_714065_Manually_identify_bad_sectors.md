---
title: "Manually identify bad sectors?"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by lloyd_b on 2008-03-03
The situation: My hard disk is slowly dying.  About two weeks ago, I picked up a bad sector.  Now it's up to 5, and I expect it to continue.

I have a replacement drive on order (it's for a laptop).  At this point, I'd just like to keep the machine working until the replacement arrives (I'm backing up critical data several times a day, just in case the drive croaks completely before the replacement gets here).

What I'd like to do is tell the system about those bad sectors, so it won't try to use them for a file.

What I've tried is (after booting from the Live CD) 
```
fsck -cc /dev/hda2
```
which is *supposed* to detect and mark those bad sectors.

But it doesn't - when it reaches the first of those sectors, "fsck" hangs, with the disk going into what sounds like a "reset heads and try again" loop.  I've let it run in this mode for several minutes, and checked "/var/log/messages" afterward - it *is* repeating the same sector over and over.

(The exact failure message:
```
Mar  1 13:13:42 laptop kernel: [21084.662951] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Mar  1 13:13:43 laptop kernel: [21084.662978] hda: dma_intr: error=0x40 { UncorrectableError }, CHS=26914/0/34, sector=6889991
Mar  1 13:13:43 laptop kernel: [21084.663005] ide: failed opcode was: unknown
Mar  1 13:13:43 laptop kernel: [21084.663022] end_request: I/O error, dev hda, sector 6889991
```)

The question: is there a way to manually tell the system that those sectors are bad?  I know the sector numbers (from "/var/log/messages"), but I don't know any way to tell the system to attach them to the "bad blocks inode".

Any hints?

Lloyd B

---

### Post by prshah on 2008-03-03
You can redirect the output with the command "badblocks -o badsectors /dev/hda2" to a file (in this case badsectors), then run fsck and tell it to use that file to identify the badblocks and mark them inactive. You will have the check the man pages for fsck/e2fsck/badblocks for the exact switch (I think it's "-l"). "-V" is your friend when running fsck.

Cheers,
PRShah

---

### Post by lloyd_b on 2008-03-03
> **prshah said:**
> You can redirect the output with the command "badblocks -o badsectors /dev/hda2" to a file (in this case badsectors), then run fsck and tell it to use that file to identify the badblocks and mark them inactive. You will have the check the man pages for fsck/e2fsck/badblocks for the exact switch (I think it's "-l"). "-V" is your friend when running fsck.

Cheers,
PRShah

Thanks for the idea, but if "fsck -cc" hangs, then I'd expect "badblocks" to do the same, as fsck with the -c option is just running the badblocks program anyway.

I may give it a try, but I'm not holding out much hope.

Lloyd B.

---

### Post by lloyd_b on 2008-03-03
As expected, badblocks locks up exactly as fsck did.

One note for anyone reading this - you *must* specify the correct blocksize when using badblocks, if you intend to feed the results to fsck.  Without this, you may wind up trashing your partition.  To find the blocksize, simply pick a file in that filesystem, and in a terminal window "stat -f {file}".

Running this *did* give me some useful info - the bad blocks start at about 3.1Gb into a 3.4Gb partition.  By cleaning out some stuff, I've got enough free space that it shouldn't even try to use those blocks.  I won't call this one "Solved", but it should be a usable work-around until that new drive gets here.

Lloyd B.

---

### Post by prshah on 2008-03-04
Yes fsck does use badblocks internally, but I thought that it may be screwing up when trying to mark the sector bad.. this often leads to an IDE reset, in which case your badblocks list may never complete... eg finds a bad sector, resets ide, finds the same one again, resets ide and so the long day wears on.

Did you try to "serialize" fsck operations? This normally is used when checking multiple filesystems and seems to be irrelevant in this case but a lot of irrelevancies are often a solution in linux, eg, xubuntu installation running slow and jerky when accessing hdd, but turns out the problem was in 24 bit video mode... changed it to 16 but and everything was peachy.

Usually, when I have bad blocks, I try to partition "around" the blocks.. do you think this may work for you?

Cheers,
PRShah

---

