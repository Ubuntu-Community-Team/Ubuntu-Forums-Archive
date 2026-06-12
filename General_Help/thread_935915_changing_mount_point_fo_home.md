---
title: "changing mount point fo /home"
date: 2008-10-02
forum: General Help
---

### Post by hirohitosan on 2008-10-02
Hi there
I create on my HDD another partition and I want to change the mount point for /home directory to my new partition. Now I have:
/dev/sda1 mount point /
/dev/sda3 mount point /home
/dev/sda5 mount point /media/disk

I want to change the mount points like this:

/dev/sda1 mount point /
/dev/sda3 mount point /disk
/dev/sda5 mount point /home

And if I change the mount points I have to create the user directories again?

Thanks

---

### Post by unutbu on 2008-10-02
Moving your /home to a separate partition is a process that requires a number of steps. Here is a guide that should help:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

