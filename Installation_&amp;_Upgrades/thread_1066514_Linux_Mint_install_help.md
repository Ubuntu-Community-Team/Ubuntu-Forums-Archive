---
title: "Linux Mint install help"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by hokie88 on 2009-02-10
So, I have tried out about 15 or so different Linux distributions and I really like Linux Mint the best I find it the easiest to use, its very stable and is a good size. Plus it took me no time at all to configure the compiz cube, my internet, and my sound so it is definitely a keeper. 

However as I am inexperienced with installing linux I formerly used wubi or live cd's or pendrive installations I am having some problems putting mint on to my computer, I would really like to use the installer that came with the software because I dont know what I am doing and don't wanna mess with all the partitioning stuff but the only option that the software gives me is to partition the remainder of my disk as mint. I do not want to do this because I have to use windows and my tablet for school everyday. So I need ample room to install many windows programs and files. I want to make Linux Mint about 15 GB of my harddrive,

So I was thinking if i filled my hardrive with say music files til I only had about 15 GB left and then installed mint it would allocate itself in the 15 GB and then I could go back and delete all that music and I would have like 30 GB of free space on the windows side again. 

Does anyone see any problems with doing it this way?

 I just don't know or have time to screw around with partitions. to Set it up manually.

---

### Post by darco on 2009-02-11
You still need to partition it since Linux uses the ext3 file system while Windows uses NTFS...15gigs isnt a whole lot of disk space for Mint. IDE/SATA HD's are getting pretty cheap now a days with the SSD drives coming out. Why not buy a cheap drive and install Mint on it then it would never interfere with your Win partition..
I am currently running Mint x64 and its very nice.
good luck

darco

---

### Post by girishsasikumar on 2009-02-11
When u say Mint should install on the free space of 15GB it means 15GB of un-allocated space, not free space in a windows drive like C: or D: and to get free un-allocated space u need to partition out ur windows drive.

Now if u feel u want to fiddle around with the partitions and install, then this is what u need to do
[LIST=1]
[*]Boot to windows and defragment ur windows drive start->programs->accessories->system tools->disk defragmenter
[*]Boot to mint live cd
[*]run linux partion editor system->administration->partiton editor (or use the command ```
sudo gparted
``` on the terminal (accessories -> terminal))
[*]use the re-size option by right clicking on the windows partition from which u want to take out ur 15GB and free out the space. Do not allocate it any filesystem like NTFS or FAT16 etc
[*]apply changes, u need to be patient, it takes time maybe a lot of it if your drive is full
[*]exit linux partition editor and then run mint install and choose to use the free space available
[/LIST]

---

### Post by hokie88 on 2009-02-11
I'm sorry I left this out it will resize my windows partition to use whatever free space is left as the linux partition so If i have 80 gigs in windows it will make Linux mint 20 GB i think that is what I am checking on. I didn't mean it would make another partition but rather risize the windows one to whatever space I had left.

---

### Post by hokie88 on 2009-02-11
> **darco said:**
> You still need to partition it since Linux uses the ext3 file system while Windows uses NTFS...15gigs isnt a whole lot of disk space for Mint. IDE/SATA HD's are getting pretty cheap now a days with the SSD drives coming out. Why not buy a cheap drive and install Mint on it then it would never interfere with your Win partition..
I am currently running Mint x64 and its very nice.
good luck

darco

I'll tell you why I don;t buy a second hardrive because I said tablet and they don't make a tablet desktop,

---

