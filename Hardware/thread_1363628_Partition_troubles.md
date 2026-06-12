---
title: "Partition troubles"
date: 2009-12-24
forum: Hardware
---

### Post by theyain on 2009-12-24
I recently bought a brand new RCA m4304-a mp3 player.  Its suppose to have four gigs of space, however the filesystem (fat32) shows it having about 3.5 gigs.  When I would open it up, gparted would only show the device as having 466 megs, it wouldn't recognize the other partition.  libparted would give the error "Can not have partition outside of partition table!" if I tried opening the device with it.  

If I ran testdisk to find and extend the partition, it would not show any partitions at all, unless I selected the option "Non partitioned media".

[See Here](http://i7.photobucket.com/albums/y263/theyain/Screenshot-5.png)

To make this story not go on forever, I eventually became feed up with it and tried to create a new partition table (using gparted) on the unallocated space.  gparted crashed, and now I can't do anything with my mp3 player :(

Any ideas?

---

### Post by ajgreeny on 2009-12-29
If you can open the player with gparted, I suggest you delete any partitions that do not contain any files or folders, which may be firmware of some sort, and try making a partition with the space which is now free.

Most mp3 players are formatted as fat32, I think so try that, or read your mp3 player manual, which may have info about reformatting if necessary; mine certainly does.

---

