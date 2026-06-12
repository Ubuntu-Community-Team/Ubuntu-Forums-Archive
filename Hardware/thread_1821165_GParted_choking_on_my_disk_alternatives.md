---
title: "GParted choking on my disk: alternatives?"
date: 2011-08-08
forum: Hardware
---

### Post by tlroche on 2011-08-08
summary: Is there a tool or tools folks would recommend for linux (specifically ext3) partition management **other than** GParted? which is failing on my disk.

details:

I need to fix the last partition in my disk (/dev/sda6), as described in [this post](http://ubuntuforums.org/showpost.php?p=11130930&postcount=1). I thought the problem was merely that GParted had hosed the primary superblock on /dev/sda6, but fixing that has not enabled me to finish this action:

> **tlroche said:**
> [LIST=1]
[*]Move /dev/sda6 [/home] to the right and shrink it. This should produce unallocated space between /dev/sda5 [swap] and /dev/sda6.
[/LIST]

I was able to "fix" the primary superblock on /dev/sda6 by using a backup superblock (as described in the following post on that thread), but that didn't help GParted much. When I restarted it, I was pleased to see that it now showed /dev/sda6 having the desired size, followed by unallocated space. So I tried to just make the free space precede the partition, which GParted interpreted as the action

```
Move /dev/sda6 to the right and shrink it from 209.32 GiB to 209.32 GiB
```

which I applied. The good news is, GParted got farther before failing; but the bad news is, it still failed. Results from Save Details follow, with steps numbered by me:

```
[1] calibrate /dev/sda6  00:00:00    ( SUCCESS )

path: /dev/sda6
start: 36837892
end: 475808627
size: 438970736 (209.32 GiB)

[2] check file system on /dev/sda6 for errors and (if possible) fix them  00:07:51    ( SUCCESS )
```

Since this had repeatedly failed previously, presumably the previous run of `e2fsck -b` silently fixed the primary superblock.

```
[3] shrink file system  00:00:34    ( SUCCESS )

resize2fs /dev/sda6 219484343K
Resizing the filesystem on /dev/sda6 to 54871085 (4k) blocks.
The filesystem on /dev/sda6 is now 54871085 blocks long.
resize2fs 1.42-WIP (02-Jul-2011)

[4] shrink partition from 209.32 GiB to 209.32 GiB  00:00:00    ( ERROR )

old start: 36837892
old end: 475808627
old size: 438970736 (209.32 GiB)
```

Which strikes me as just odd: isn't "shrinking" from one size to **the same @#$%^&! size** a no-op? How could that possibly fail? But it did! apparently unmounting /dev/sda6, and hosing all subsequent steps in that action. So I'd now like to know,

[LIST=1]
[*]How could GParted possibly fail step 4? To "shrink partition from 209.32 GiB to 209.32 GiB" sounds like a NOP to me--am I missing something?
[*]How to get GParted over that hurdle? Or should I use another tool?
[/LIST]

---

