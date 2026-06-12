---
title: "partition xp drive with Partition Magic or GParted?"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by tripler on 2009-09-25
I'm installing Ubuntu 9.04 on a laptop which already has xp pro. I need to resize a partition. Am I better off doing it from inside windows (looks very easy) with Partition Magic 8.0 or booting off GParted Live CD 0.4.6-3 (looks harder). 

Currently there are 3 partitions, all primary: 
Dell Utilities - 40MB used, 30MB free
XP - 15GB used, 40GB free
unallocated - 2.5GB free

I want to give Ubuntu 30GB, resizing the unallocated partition and taking the extra space from the xp one. Everyone seems to use GParted - is it much better? Partition Magic looks simpler to me, who is pretty much a novice user.

And should I make the Ubuntu partition logical or primary; NTFS or Ext2 or Ext3?  I'll add the individual Ubuntu partitions later, when installing it.

One other thing, is it worth having a fourth partition in NTFS for docs which both xp and Ubuntu may want to access?   

Thanks!

---

### Post by Partyboi2 on 2009-09-25
I personally use gparted, so I would recommend it, but you should be able to use either one.
I would create a extended partition and install Ubuntu to logical partitions under the extended partitons since you can only have a max of 4 primary partitions and creating a extended partition gets around this.
If you plan to swap files between Windows and Ubuntu I would recommend having a ntfs partition for this as Ubuntu can read/write to ntfs but Windows can not read/write to ext partitons (without extra software).

---

### Post by Herman on 2009-09-25
:) I agree with Partyboi2 and I would like to add that if I were a Windows user, the main reason I would want an extra partition for sharing/transferring files between Ubuntu and Windows would be to allow the said files to be scanned for viruses before being opened by any Windows programs or before being transferred into Windows. Viruses can't run in Ubuntu but they can be passed though Ubuntu if you're not careful.

Regards, Herman :)

---

### Post by stinger30au on 2009-09-25
use the gparted on the ubuntu live cd and you will be right as rain

---

### Post by tripler on 2009-09-26
In the end I used GParted and everything was fine. It is pretty user friendly once you're inside.

I didn't know it's on the Ubuntu 9.04 live CD. Would have saved a burn. How do you get to it from there?

---

### Post by raymondh on 2009-09-26
> **tripler said:**
> 
I didn't know it's on the Ubuntu 9.04 live CD. Would have saved a burn. How do you get to it from there?

Run a live session (try ubuntu without changes) > system > administration > partition editor (gparted).  Albeit, a standalone gparted disc is a good tool to have as well.

---

