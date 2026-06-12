---
title: "Missing LVM Tools - vgsync &amp; vgreduce to clean up extent duplication from pvmove"
date: 2008-07-26
forum: General Help
---

### Post by j0nny55555 on 2008-07-26
My 1st post!  I would like to give a big thank you to the community for helping it get this far and hopefully I can help a little here too.  If you know a LOT about LVM then please skip to the bottom and see if you know the answer to the question - everything else is superfluous in case you feel that my question is stupid or want to know why on earth I would be asking this.

Recently I started adding larger hard drives to my LVM and removing some of the plethora of smaller 80 and 120 GB HDs so that I could fit this server into its box (currently its 10 HDs and no case to fit them all).

The problem started when I added an otherwise good looking Western Digital 160 GB HD and then that drive started to reset.  After checking out the "nodma" option you can add to your kernel parameter in the menu.lst for grub I then set the UDMA and DMA modes with "/etc/hdparm.conf" on the problematic HDs for optimal up-time (once the HD resets it tends to crash the whole OS) I finally completed an:

```
fsck -fyv /dev/lvmvolume/lvmstore1
```

The data is there and usable, I was able to play a couple movies and see some data that was added only days before.  The issue is that when I added the 160, I already had about 100 GB free and now I basically have only 100 GB free and I should have about 260 free.

Here's what started the problem:

```
pvmove /dev/sde
```

When it started, the new Western Digital (/dev/hda) HD actually hiccuped in the first maybe 15% of the pvmove process and now I have about 70 or so GBs (huge estimation) of duplicated extents that I would like to clear out.  There seems to be a few tools that HP UX has developed for their LVM2 support that we are maybe missing or have been redeveloped in other methods or tools that I haven't found yet.

Here's what I've found that seems to be archaic or just only for the HP UX platform:

[INDENT]+ vgsync (clears out the extra extents that have been duplicated

+ vgreduce -m 1 volumename (clears out the extra mirrored extents - if you ever started a vgmove and saw it crash, this will clear out your mirrored extents and is something i need to do an then remove the dying hd).[/INDENT]

In the end my question is where are these tools or is there another way to remove duplicated extents also known as mirrored extents from your LVM volume?

---

