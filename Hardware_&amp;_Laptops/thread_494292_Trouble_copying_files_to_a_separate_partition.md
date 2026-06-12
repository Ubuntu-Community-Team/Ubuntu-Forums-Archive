---
title: "Trouble copying files to a separate partition"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by PrestonHerrmann on 2007-07-06
Recently, I had been messing around with Linux, and accidentally formatted my windows drive. After deciding to switch to linux, I also decided to partition my 80 gig drive into three separate partitions, two 4 GB, one for linux OS, and the other for Windows, and left the remaining partition as a fat32 partition, which could be accessed from both OS, for things such as music and whatnot. When I formatted my windows drive, i lost all my music. Thankfully, it was all backed up on my Creative ZEN, and an still access it there. But the trouble I am having is copying the music back to the fat32 partition. When I used gnomad or Amarok to copy the songs, it fills up the OS partition, not the separate partition, which has a good 60+ gigs left. The only way to navigate to these partitions to save was through this path "/media/sda3", which is going through the File System partition. Like I said, the file system partition is only 4 gig, but the sda3 partition is 60gigs, but the files quit copying once the file system partition fills up. Is there any way to directly copy these files to the sda3 partition and bypass the file system partition?

I realize that this is very VERY complicated, but if anyone else has had this problem, it should make it a bit easier to understand

---

### Post by yorkie on 2007-07-06
Hi
Have you tried drag & drop with your music files sometimes the simple ways work.
also you didn`t mention a swap partition.
do you see the fat32 partition  in places or on the desktop

---

### Post by PrestonHerrmann on 2007-07-06
I can see the 60 gig partition on the desktop and in "places", and to the drag and drop idea, the files show up on the sda3 60 gig partition as well, so they're going to the right place, but the programs I use to transfer them wont let me add any more, seeing as the file system partition has already reached its max due to the 60 gig partition being included under the the 4 gig file system directory. 

[http://picasaweb.google.com/PrestonHerrmann/UntitledAlbum/photo#5084267149245016418]("http://picasaweb.google.com/PrestonHerrmann/UntitledAlbum/photo#5084267149245016418")

if you can't see it all, try the magnification button in the upper left

here, you can see how sda3 is just a sub-directory of the main 4 gig partition. Even though the size of the sda3 partition is 60 gig, the 4 gig partition its apart of is limiting the amount of files i can put it

---

### Post by yorkie on 2007-07-06
your set up is the same as mine for some reason FILESYSTEM does not show in media I think your problem is your linux partition is too small it should be at least 10gig try resizing 60gig partition say to 50 gig then resize  linux partition up then all will be o`k
goodluck

---

