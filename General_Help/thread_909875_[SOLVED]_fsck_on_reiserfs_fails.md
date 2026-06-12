---
title: "[SOLVED] fsck on reiserfs fails"
date: 2008-09-04
forum: General Help
---

### Post by angryhomer17 on 2008-09-04
It seems my sata hdd failed today. I was listening to some music from the drive and it just stopped. 

So I tried a reiserfsck /dev/sdb1 which fails to 
Bad root block 0. (--rebuild-tree did not complete) Aborted

So then I tried resierfsck --rebuild-tree /dev/sdb1

```
The whole partition (122096000 blocks) is to be scanned
Skipping 11937 blocks (super block, journal, bitmaps) 122084063 blocks will be read
0%....20%..     .                                                  left 0, 15514 /secccseccccc
Could not find a hash in use. Using "r5"
Flushing..finished
	Selected hash: "r5"
	Read formatted blocks: 122084063
	Objectids found: 2
Pass 1 (will try to insert 0 leaves):
####### Pass 1 #######
Looking for allocable blocks .. finished

Flushing..finished
####### Pass 2 #######
Flushing..finished
	Objectids found: 2

No reiserfs metadata found. 
```

debugreiserfs /dev/sdb1 shows
```

Filesystem state: consistency is not checked after last mounting

/dev/sdb1: Reiserfs super block in block 16 on /dev/sdb1 of format 3.6 with standard journal
Count of blocks on the device: 122096000
Number of bitmaps: 3727
Blocksize: 4096
Free blocks (count of blocks - used [journal, bitmaps, data, reserved] blocks): 122096000
Root block: 0
Filesystem is NOT clean
Tree height: 65535
Hash function used to sort names: "r5"
Objectid map size 2, max 972
Journal parameters:
	Device [0x0]
	Magic [0x0]
	Size 8193 blocks (including 1 for journal header) (first block 18)
	Max transaction length 1024 blocks
	Max batch size 900 blocks
	Max commit age 30
	Max transaction age 0
Blocks reserved by journal: 0
Fs state field: 0xfa02:
	FATAL corruptions exist.
sb_version: 2
inode generation number: 0
UUID: <no libuuid installed>
LABEL: 
Set flags in SB:

```

I tried rewriting the superblock, tried scanning the whole partition, tried --fix-fixable.

I saw that there is a bug in reiserfsck 3.6.19 that is causing the abortions. I installed 3.6.20 from source and ran everything again but it still failed.

Short of repartitioning/formatting the hdd, I am unsure of what to do. I do have a pretty good bckp of the drive but it's not easily accessible now. Any suggestions of how to get the drive working again? I only got this drive a year ago and it has shown no signs of failure during the time I've used it. 

Thanks for any help.

---

### Post by angryhomer17 on 2008-09-04
Ok, I still have no idea what happened, but I fixed the drive. It appears everything is still intact.

So part of the problem was that I don't think the drive was ever a reiserfs, it has always been ext3. When I reformatted my first drive I changed it from ext3 to reiserfs and the same with my laptop.

So, whatever caused the problem in the first place was further hurt by me trying to fix an ext3 system with reiserfs tools. :(

I used testdisk to see if I could fix partitioning problems, which showed an ext3 fs, and also a reiserfs with the same data. Really didn't get anywhere with that.

dmesg| tail also showed problems with an ext3 fs, so I figured it really was supposed to be ext3. 

I used this website for what I thought were reiserfs problems
[http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html](http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html)

And this for my ext3 probs
[http://www.nabble.com/Bad-magic-number-in-super-block-td13008360.html](http://www.nabble.com/Bad-magic-number-in-super-block-td13008360.html)

I had this prob with running fsck.ext3 which the above forum helped me with.
fsck.ext3: Bad magic number in super-block while trying to open /dev/sdb1

I finally ran fsck.ext3 on the drive and fixed all the messed up blocks. 

So yeah, the moral of the story is to remember your fs's. Hope this helps any idiots like me.:)

---

