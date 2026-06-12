---
title: "softraid horror stories!"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by moonlightcheese on 2008-02-21
i was thinkin to solicit some horror stories on softraid as i have already experienced a full on array death due to just not knowing what to do.  now that i've done some reading, i feel like i know a little more about what i'm doing but there's still a level of ambiguity.  i'd like to get enough information to write a raid guide for the forum since i'm not really satisfied with any of the guides i've seen.  it seems like people just sat on the toilet and out came a nice, brown user guide...  (that's not to say it's all like that, but some of these guides could use some TLC)

SO, please share (in as much detail as you can please) your softraid horror stories and how you fixed them!  hopefully this will save a lot of ubuntu end users some serious headache

[mystory]
i setup a raid5 with mdadm with 3 seagate 320GB 7200.10's and then i received the 4th disk back from RMA.  well... you can't add disks to a raid5 without rebuilding completely in mdadm but i had too much data on that array.  here's what i ended up doing.

- copy as much as possible to another pc and the RMA drive i just got back (~520GB)
- drop the array with 3 disks
- build a 4 disk array missing a single drive
- copy data from other drives back to the new raid5
- format 4th disk
- add 4th disk to array
[/mystory]

anybody notice a step i missed?  it's a pretty important step and it isn't mentioned in ANY of the guides in the documentation iirc.  when you are building an array, to be safe, **ALWAYS ZERO THE SUPERBLOCKS**.  superblock data is written when the array is created but once the array is dropped, that superblock information is not erased and is scattered at various byte intervals all over the disk.  run this command:
```
mdadm --zero-superblocks /dev/*device*
```
to erase all superblock data on the drive.  also, it may be worth your time to go ahead and perform a FULL format before building the array, or you can just find the start of the space you want to use and write zeros over all the blocks you want to use with 'dd'.  if you don't know what 'dd' is, google 'man dd'.

depending on how much info is in this thread and how much i can scour up, i'll try to write a TRULY fool-proof guide to raid... because it's just too easy to mess up a softraid... and after losing 520GB of data, i'm pretty sore about it.

---

