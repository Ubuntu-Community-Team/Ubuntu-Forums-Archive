---
title: "Trouble mounting windows 'Dynamic Disk'"
date: 2009-05-15
forum: Hardware
---

### Post by kai.scorpio on 2009-05-15
I have a bit of a tricky situation concerning HDDs.

I have one disk set up as a 'Dynamic Disk' in Windows, which I used to be able to mount from dolphin without any setup or errors. I replaced the other HDD in my computer with a larger one, and now this Dynamic Disk doesn't show up in either windows (Labeled 'Invalid' in the storage manager) or kubuntu (nothing happens when I try to mount it in dolphin, it just dumps me back to my previous directory without an error).

It is still present in bios, and /dev/disk/by-id it shows up as four entries, ata-Maxtor..200.., Maxtor..200..-part1, and those two with the prefix scsi-1 (I think this is it, as it is my only maxtor 200 GB drive).

I don't really know my way around the terminal, so is there any way to get at the data on this?

---

### Post by kai.scorpio on 2009-05-15
Updating to 9.04 has fixed this. I don't know if its a new software, or if something was reset during the upgrade.

Next step is to see how to get it to work in Windows, but if anybody has any advice about this topic please post it.

Thanks,
Kai

---

