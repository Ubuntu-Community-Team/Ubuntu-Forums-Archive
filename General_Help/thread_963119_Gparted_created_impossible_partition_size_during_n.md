---
title: "Gparted created impossible partition size during ntfs resize"
date: 2008-10-29
forum: General Help
---

### Post by pseudolobster on 2008-10-29
I recently added a drive to my RAID-5 array and wanted to expand the partition to use the new space I had, so I booted off a partedmagic cd and resized the partition to 2.5tb...

I found out afterwards that the max partition size supported by MBR partition schemes is 2tb. Unfortunately, gparted didn't know this and happily resized anyways... Now, instead of a 2300gb ntfs partition, I have a 230gb partition that fails to mount... gparted tells me the drive is detected incorrectly and refuses to touch it, ntfsresize won't either till I expand the partition it's within (not possible on an MBR partition), a windows recovery console's DISKPART tells me "the volume contains one or more unrecoverable problems"..

basically, I have an NTFS volume containing 1.6tb of data, that's contained within a 2.3tb partition that's detected as 230gb... The data is intact, in fact I can even get halfway through booting windows before it references a file past the 230gb boundary... I just can't figure out how to resize the partition back to <2tb, then resize the ntfs volume accordingly.

I thought I could do this in parted, then ntfsresize, but parted tells me ntfs support isn't implemented yet. *groan* ](*,)

RAID controller is a Dell Perc5/i, so any suggestions anyone has must either involve a windows recovery console, or a linux distribution that includes the megaraid_sas module.

Thanks!

---

### Post by fjgaude on 2008-10-30
My only comment is regarding the **importance** of always having **backups** for important data. I have three, one online, one near-line, and finally, one off-line.

---

