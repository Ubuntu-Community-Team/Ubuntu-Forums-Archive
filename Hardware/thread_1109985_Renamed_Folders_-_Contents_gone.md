---
title: "Renamed Folders - Contents gone"
date: 2009-03-29
forum: Hardware
---

### Post by pmeng on 2009-03-29
Hi all,

My brother renamed 3 Folders on his external Harddisk (connected via USB2.0) and somehow, after renaming these Folders, the contents were gone. I told him to immediately stop working with that Harddisk, and cloned the whole partition with dd to a dump-file on another Harddisk.

I am quite familiar with Foremost, but the problem is, that there were a lot of files, where Foremost don't know the headers yet.
So i wanted to ask you if there is a way to get the data back from these corrupted directories.

It is a FAT32 (LBA) partition. I already tried fsck.msdos -n on this drive, and it told me that the directories are in a wrong place (but i didn't let it fix it, because i don't know if this would bring back data)

Now i am running Testdisk, it is currently looking for root clusters, and it shows me every few minutes a list of files it found (the lost files), but i can't find a way to copy them to a save place.

Does someone have an idea what i can do to get back to that data?

Thanks a lot!

[Using Ubuntu Intrepid]

---

