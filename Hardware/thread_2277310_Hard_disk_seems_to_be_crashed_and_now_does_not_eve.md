---
title: "Hard disk seems to be crashed and now does not even show up"
date: 2015-05-08
forum: Hardware
---

### Post by kisun on 2015-05-08
Hi,

I have two hard disks in my computer and the one that I mainly use for my work seems to be crashed when I upgraded to Kubuntu 15.04. My bad, I didn't backed up the data. Is there any way to recover data from that hard disk? It has some very important files. Any help would be appreciated. Thanks!

---

### Post by andybuckle on 2015-05-08
So, the system still boots? Just a data disk down?

I had some luck with ddrescue in the past. Try to use it to copy the partition to an external disk.

---

### Post by sudodus on 2015-05-08
Welcome to the Ubuntu Forums :-)

I would try ***testdisk*** and ***photorec*** from [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

1. ***If the data are very important***, I suggest that you stop using the crashed drive at once, and that you make a cloned copy of it to a 'third' drive,

- use ***ddrescue*** to create a cloned copy of what can be recovered (still no explicit files).

2. The next step is to use ***testdisk*** and try to recover the file system from the 'ddrescued' cloned copy.

3. If that does not work, use ***photorec*** and try to recover the files directly from the data stored on the 'disk surface' without a file system. It is hard and messy work, but you will be amazed how much that is possible to recover (if it is not already overwritten).

Good luck :-)

---

### Post by kisun on 2015-05-08
I am able to boot the system because i have another ssd where linux is installed. The main problem is the second hard disk is not discoverable (using lshw -C disk and fdisk -l) because of which neither ddrescue nor testdisk works. :(

---

### Post by sudodus on 2015-05-08
I see. That makes things more difficult. I think there are tools, that specialist companies use for such cases, but I don't know any details.

---

### Post by andybuckle on 2015-05-08
You could pay someone to do it (lots of money), or you could have a go at opening up the hard drive to see what is wrong. There are video tutorials on youtube for this kind of thing. Never had to do this myself.

eg
[https://www.youtube.com/watch?v=F5Y7BniaRXg](https://www.youtube.com/watch?v=F5Y7BniaRXg)

---

