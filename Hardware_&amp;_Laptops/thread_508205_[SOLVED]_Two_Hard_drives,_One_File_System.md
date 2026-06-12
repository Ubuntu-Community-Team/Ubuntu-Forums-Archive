---
title: "[SOLVED] Two Hard drives, One File System"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by gali98 on 2007-07-23
I have a very old computer (Pentium II, 333 megahertz, I upgraded to 512 RAM I had laying around, 1998 ) that I installed Ubuntu studio onto. The only problem is that my BIOS won't detect, my 30 gig hard drive. So I installed it onto a little 6 gig one. It boots fine and everything works great. I can get to my other hard drive once linux boots. I've been reading a bit about linux ( I'm kind of new and all) and I saw something about how the file system doesn't have to be a single hard drive, it can be multiple places, regardless of distant and such (however it was more for a business person who would have an administrator do such things for them and did not tell me how.)  I know sooner or later I will use up 6 gigs, so here's my question: can I mount this 30 gig hard drive in way that it just becomes an integrated part of my file system, without being mounted to a specific folder such as /home/kory/mount_folder/yada yada, but instead, so that once the 6 gigs were up I could install more software, and stores files in any place I wanted, and have it basically just using both as one file system. Okay I think that is explainable to most 5 year olds, so I will leave it at that. Any help would be appreciated. 
Thanks
Kory

---

### Post by zanglang on 2007-07-24
Some of the more advanced filesystems do support "pooling" multiple drives into a "logical" volume. I've read that LVM and EVMS (and more recently, ZFS) would do the trick nicely... maybe you'd be interested in the following articles.

EVMS: [http://en.wikipedia.org/wiki/Enterprise_Volume_Management_System](http://en.wikipedia.org/wiki/Enterprise_Volume_Management_System)
LVM:
[http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)
[http://tldp.org/HOWTO/LVM-HOWTO/whatisvolman.html](http://tldp.org/HOWTO/LVM-HOWTO/whatisvolman.html)
[http://www.ibm.com.nyud.net:8080/developerworks/linux/library/l-lvm/](http://www.ibm.com.nyud.net:8080/developerworks/linux/library/l-lvm/)
[http://www-128.ibm.com.nyud.net:8080/developerworks/library/l-lvm2.html](http://www-128.ibm.com.nyud.net:8080/developerworks/library/l-lvm2.html)

---

### Post by gali98 on 2007-07-24
Thanks, for answering, I'll check it out and see what I can do.

---

