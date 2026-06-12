---
title: "Seperate Home Partition"
date: 2008-08-15
forum: General Help
---

### Post by RATM_Owns on 2008-08-15
Yes, I read this already: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

But I was wondering, is the trouble (very little trouble) worth it?

And how much GB should I leave for /?
My hard drive is 250GB.
Ubuntu has 220.5GB of it. (I was thinking about moving around the partitions to get more space for Ubuntu)
And I already have the max 4 physical partitions.

---

### Post by Elfy on 2008-08-15
You can apparently convert a primary to an extended thus getting round the max 4 partitions thing.

I have a 10Gb / which is about half full.

I used to have a seperate /home but after a slight accident ;) I moved away and now have the majority of my data on seperate partitions which I mount with fstab. Although I do still have a small /home it will go eventually and I will only keep configs in there.

As to whether it is worth it - that can only really be answered by you - I used to think so, but less so now.

Hope that helps some.

---

### Post by mojoman on 2008-08-15
I used to have a separate /home but right now I don't. If you muck about a lot, experiment and break stuff it's usually a good idea. Same if you do a lot of re-installs (for whatever reason) and like too keep documents and settings. If you're distro hopping a lot it might also be a good idea but if you'd like to use several distros at once I personally prefer to use the root for home and keep a separate partition which I mount in /home/documents for, well, documents and stuff. That way I can keep separate settings for my separate distros and still have access to my documents. I also have separate partitions for stuff like movies, music and whatnot that the different users need to share. If you want to access your mail through several distros without having a common /home this can be fixed by linking the folders.
/mojoman

---

### Post by Oldsoldier2003 on 2008-08-15
Personally I prefer a separate data partition I don't bother with a separate /home anymore. Of course your mileage may vary...

---

