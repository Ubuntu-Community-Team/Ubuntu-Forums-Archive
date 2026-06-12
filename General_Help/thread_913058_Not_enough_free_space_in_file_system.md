---
title: "Not enough free space in file system"
date: 2008-09-07
forum: General Help
---

### Post by Jaget on 2008-09-07
Hey, i installed ubuntu yesterday. It runs great, so i was wanting to transfer all my music from xp and save it so i can have it on ubuntu. I have all my music on my external HD (about 20 gigs or so) and thought i'd just be able to save it back onto this. However the file system only has 5gb of free space, even though there's about 80gig free on my hard drive. 
Could this be to do with the way i installed ubuntu and maybe have not allocated it enough disc space and is there anyway i can make the file system have more free space so i can transfer all my muisc?

---

### Post by Sycron on 2008-09-07
Yoe need to boot from the livecd and resize the filesistem partition with gparted.

Type in a terminal:```
gksudo gparted
```

---

### Post by wolfen69 on 2008-09-07
download the [Gparted Live CD]("http://downloads.sourceforge.net/gparted/gparted-live-0.3.7-7.iso?modtime=1215010676&big_mirror=0") and use that to resize your partitions.

---

### Post by wolfen69 on 2008-09-07
> **Sycron said:**
> Yoe need to boot from the livecd and resize the filesistem partition with gparted.

Type in a terminal:```
gksudo gparted
```

hardy does not come with gparted. although it can be downloaded in the live environment.

---

### Post by Jaget on 2008-09-07
I have installed gparted, but im not really sure what parts to resize. I'll take a screenshot; [Click](http://img397.imageshack.us/my.php?image=screenshotdevsdagparteddt1.png).

---

### Post by wolfen69 on 2008-09-07
there is a pull down menu in the upper right to select which drive you want. then just select which partition you want to resize.

---

### Post by Jaget on 2008-09-07
But which partition is the correct one to resize?

---

### Post by Sycron on 2008-09-07
I'm sure that would NOT be a fat16/fat32 or NTFS one. It should be ext3 and to have mountpoint / .

---

### Post by Jaget on 2008-09-07
I only have one harddrive though  - those are the only availabe partitions :/

Hmm, maybe i should've mentioned that when i installed ubuntu i just mounted the iso file and chose to install inside windows. I didn't create a live CD and run ubuntu off that when i started up.

---

### Post by Elfy on 2008-09-07
That's a wubi install - it can help to let people know, when people are replying generally it would be expected that you have a normal installation.

Resizing the partition for a wubi install is different, this is the resize page from the wiki

[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I resize the virtual disks?

The wiki page is 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Jaget on 2008-09-07
Thanks a lot. Should hopefully be able to do it from here. I've at least managed to create a partition thats ext3. Should be able to figure it out from here.

Sorry being unclear at the start.

---

### Post by Sycron on 2008-09-07
> **Jaget said:**
> Thanks a lot. Should hopefully be able to do it from here. I've at least managed to create a partition thats ext3. Should be able to figure it out from here.

Sorry being unclear at the start.

Yeah it's bad to write very very long phrases without paragraphs.

---

