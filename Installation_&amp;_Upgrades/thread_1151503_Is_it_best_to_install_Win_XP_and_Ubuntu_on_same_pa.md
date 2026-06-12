---
title: "Is it best to install Win XP and Ubuntu on same partition or 2 partitions"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by camino3701 on 2009-05-07
I intend to try and install Win XP and Ubuntu on the same computer hard drive. Should I install them both on the same partition or partition the hard drive which I've never done. the hard drive is 300gig in desk top. Any advice will be appreciated.
Thank You,
RLB

---

### Post by Partyboi2 on 2009-05-07
For better performance installing Ubuntu to its own partitions would be the way to go. But if you do not feel comfortable installing Ubuntu to its own partitions then use wubi to install ubuntu on the same partition as windows.

---

### Post by Mark Phelps on 2009-05-07
Understand that when you install MS Windows and Ubuntu to the same partition, you are basically installing Ubuntu inside windows as an application.  It's not really a separate installation.  So, there will be some performance hit from doing this.

---

### Post by zero7404 on 2009-05-07
not sure what tools are available to u for shrinking your XP partition, but i'd highly recommend you shrink the partition down by at least 10 GB for installing ubuntu.

i have a 320GB hdd that i split in the middle between vista and ubuntu...150GB for each OS.

best way is to leave the space as unallocated, then do a manual create of the partition when installing ubuntu. also keep in mind you'll need to create a swap partition, about 1-2GB for ubuntu.

<although i have never seen my installation make use of it, ppl say it is needed>

---

### Post by camino3701 on 2009-05-07
Thank for the advice. What and how is the best way to create 2 partitions? One for XP and one for Ubuntu.

RLB

---

### Post by HyRax on 2009-05-07
The Ubuntu installer will shrink the XP partition for you. By default it will split your hard-drive in two (assuming there's anough space to do that).

---

### Post by elliotn on 2009-05-07
Partition the drive or give ubuntu 5gb if u are not used to it, but if ur comfortable with ubuntu thex give a big partition

---

### Post by gta117 on 2009-05-08
> **elliotn said:**
> Partition the drive or give ubuntu 5gb if u are not used to it, but if ur comfortable with ubuntu thex give a big partition

Thats what I did. I gave ubuntu 120 gigs out of 160. 20-30 of that is for windows. the rest I do not know what happened to it. Something is wrong. I already posted it in another thread. Its right at the top, trying to install windows for duel boot.


As for the part: if you are going to use ubuntu for everything but a few apps and games, give it the main booty.


-gta117

---

### Post by camino3701 on 2009-05-08
Thank you all
RLB

---

### Post by zero7404 on 2009-05-08
> **gta117 said:**
> Thats what I did. I gave ubuntu 120 gigs out of 160. 20-30 of that is for windows. the rest I do not know what happened to it. Something is wrong. I already posted it in another thread. Its right at the top, trying to install windows for duel boot.


As for the part: if you are going to use ubuntu for everything but a few apps and games, give it the main booty.


-gta117

have you looked in administrative tasks->disk management in windows to see what is allocated and what is not ?
you can also see unallocated space in gparted (system->administration->partition editor).... you can choose the disk if you have more than 1 in gparted, it's selectable in the upper right hand part of the window....

---

