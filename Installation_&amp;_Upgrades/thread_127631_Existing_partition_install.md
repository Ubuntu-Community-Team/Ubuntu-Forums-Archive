---
title: "Existing partition install"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by skivtmp on 2006-02-09
Hello!  I currently run Windows XP Home Edition SP2 on a Dell Dimension 8200 with an 80 gig hd.  I have two equal sized partitions, both NTFS, one for the actual operating system and the other for all my data (documents, music, pictures, etc).

I need to install Ubunto for an Operating Systems course, so I allocated 6GB of space off of my C: drive (op sys) and formatted it for ext2.  I am now trying to install Ubunto and when I am asked what to do for partitions, I say manual.

My partitions are displayed however I have not created swap space.  In trying to reallocate more space off C: for swap space, when selecting "Finish and write changes to disk" the process starts but quits immediately saying that "there is no root file system selected, please go back and correct".  Now back at the partition window, the error message repeats regardless of what partition I try (I tried changed the 6GB from ext2 to FAT32 just to see but the same message came up).

I had to abort the installation and can't seem to figure out what I need to do.  I've looked through other posts but have not been able to find a direct match.

Any help would be great!

---

### Post by jonathanm on 2006-02-09
You need three partitions for ubuntu not one.  on the install menu where it asks you to partition go into the partition that you set aside for ubuntu and set the mountpoint or 'use as' (i cant remember) as / (root partition) then sort out a swap partition and boot partition (actually, not sure if you need a boot partition, dont take my word for this though) using the same method.

---

### Post by Greg2 on 2006-02-09
Here’s an easy how-to that Herman has put up on his web site:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

