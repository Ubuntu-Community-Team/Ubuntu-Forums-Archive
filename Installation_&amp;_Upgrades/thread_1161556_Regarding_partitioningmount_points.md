---
title: "Regarding partitioning/mount points"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by hackapelite on 2009-05-16
So, I have two hard drives, one 320GB and one 500GB. Now, Ubuntu doesn't take up all that much space, it wouldn't make sense to me to allocate all of even the small drive for it... so would it be possible to, say, mount a 80GB partition of the 500GB drive as /, the 320GB drive as /home and the rest of the 500GB drive as /home/qwerty, where 'qwerty' is my would-be user name? So basically, my account would get a dedicated 420GB (roughly) partition, and the 320GB would be shared among all other users?

In essence, why I'm asking this is... I don't know if the installer would fail when it creates the folders for the users, if there's already a mount point under the user name. Anyone know if this would work?

---

### Post by Partyboi2 on 2009-05-16
Hi, 80 gig is a lot to give to / you could always make that smaller if you are worried about space.
You can create the /home partition when installing and set qwerty as the user, then after the install is complete add additional users that will have their folder on the /home partition.

---

### Post by hackapelite on 2009-05-16
> **Partyboi2 said:**
> Hi, 80 gig is a lot to give to / you could always make that smaller if you are worried about space.
You can create the /home partition when installing and set qwerty as the user, then after the install is complete add additional users that will have their folder on the /home partition.I'm not worried about space at all ;) What would be a good size for '/', though? 40GB? I want to be sure that it never gets full, but also I don't want to *waste* my HD space.

As for the rest, that's what I always do; I was just wondering if it's possibly to create a separate partition for one user (using the method I described), so /home would be a separate partition and /home/qwerty another, so all users except qwerty share the same partition?

---

### Post by tragicglee on 2009-05-17
> **hackapelite said:**
> I'm not worried about space at all ;) What would be a good size for '/', though? 40GB? I want to be sure that it never gets full, but also I don't want to *waste* my HD space.

As for the rest, that's what I always do; I was just wondering if it's possibly to create a separate partition for one user (using the method I described), so /home would be a separate partition and /home/qwerty another, so all users except qwerty share the same partition?

Even a 40GB partition for / strikes me as excessive. I guess it depends on  what you've got installed, how frequently you install new things, and what you use the system for, but still! Run df -h, see how much space you're using on / and use that as a guide.  I decided to be *generous* with / during my last install -- I gave it 8GB, and I've still got nearly 5GB free (exactly 4.9). Granted, I havent gotten around to reinstalling a lot of apps, but I can't remember ever really using more than 4 or 5 (gigs, not apps :P) 

Splitting home directories over two partitions is possible. I've done it in the past, when I had 7GB *total space* split over two drives, and was dual booting another distro and XP. I've never had reason to do it under Ubuntu, so I'm unsure how the installer will react but it shouldn't give you problems. IF it does, just edit fstab, and manually set qwerty's home directory through Preferences -> Administration -> Users & Groups (or usermod, if you prefer the terminal)

---

### Post by hackapelite on 2009-05-17
> Even a 40GB partition for / strikes me as excessive.:o
I wasn't sure if 40GB would be enough, so I made it 60GB... well, I know better now :p


> Splitting home directories over two partitions is possible.I've got that sorted out now ;)

---

### Post by Trigsu on 2009-05-17
I'm lending the topic:

I have 2 hard drives, 250GB and 1TB. I'm going to format smaller one and splitting it for XP(40GB), W7(50GB), Ubuntu(recommendations?) and there will be some free space after those.
How many partitions Ubuntu actually makes/needs and what's their use?

---

### Post by hackapelite on 2009-05-17
> How many partitions Ubuntu actually makes/needs and what's their use?How many does it need? Two; '/' and swap (AFAIK Linux uses the swap area to store the contents of memory when hibernating - at least Fedora did; that in addition to the fact that some swap is always a good thing to have). However, for convenience, most people have three: '/' (which is usually rather small, 10GB appears to be alright for what I've learned in the course of this thread), '/home' (Documents and Settings [XP] / Users [Vista] esque) that takes up almost much all the space, and a small swap partition - depending on how much memory you have. Personally, if I have less that a GB of RAM, I create a swap twice as big as my RAM; otherwise, I make it equal the size of my RAM.

EDIT: Those three in addition to all possible Windows partitions (dualbooting, storage etc.), of course.

---

