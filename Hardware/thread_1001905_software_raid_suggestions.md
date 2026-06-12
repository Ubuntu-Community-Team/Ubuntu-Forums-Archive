---
title: "software raid suggestions"
date: 2008-12-04
forum: Hardware
---

### Post by Apocrathia on 2008-12-04
I have 2 1.0tb drives that I want to raid together, however my sata card is a fakeraid card. I want to do a software raid that I can grow in the future. Does anyone have any experience with dmraid or mdadm? because even after reading numerous articles, they make no sense to me.

---

### Post by andreasis on 2008-12-04
I'm assuming that you want to set up software raid on Ubuntu.  You can do this by using the alternate cd, as opposed to the desktop/live cd.

Do you have experience using the alternate cd?

(I'm successfully running a 500GiB+500GiB raid0 under ubuntu)

[EDIT] do you use the server edition of ubuntu?

---

### Post by Apocrathia on 2008-12-04
I'm running ubuntu desktop. I have the boot data on a seperate 120gb drive and the two terras are just for storage and I really don't want to have to redo my install. I used wubi for the initial install and moved it over to a dedicated drive using lvpm.

---

### Post by Apocrathia on 2008-12-04
The entire raid will just a network storage device, shouldn't I be able to set all of this up from within the operating system? Is there any sort of GUI-based tools that I can use that I haven't found yet?
I have the two drives in a 3 x 5.25 -> 4 x 3.5 bay sata backplane, that way I can add more storage to it in the future whenever I manage to fill 2 terrabytes. I just want a to software raid the two drives that are in there now to one drive that I can later grow to a 3rd or 4th drive. I've been thinking about just keeping the drives all seperate but that's the problem I'm having now, is all of my data is scattered across my network and I need it all just to be in one place.

---

### Post by andreasis on 2008-12-05
I don't mean to insult your intelligence, but this is the help that I am able to offer at this point. 

I am aware that fdisk [http://www.youtube.com/watch?v=miQaIabR1Dw](http://www.youtube.com/watch?v=miQaIabR1Dw) is able to set up sata partitions, but it's not gui.

gparted is a gui formatting program, but I am unsure on its effectiveness with RAID.

The most I can do is what you can do too: google linux raid, ubuntu raid, and anything more specific.  Hope someone else will be able to add some more to this.

---

### Post by iggykoopa on 2008-12-05
look into system-config-lvm I've used it in the past and if you know the basics of lvm then it makes it a lot easier to configure an array. This is the only gui raid tool I've found but it works pretty good, if your running intrepid it's in the universe repos.

---

