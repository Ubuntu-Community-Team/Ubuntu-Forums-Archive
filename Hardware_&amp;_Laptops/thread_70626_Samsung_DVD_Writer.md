---
title: "Samsung DVD Writer"
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by Kimm on 2005-09-30
Yesterday was my birthday and I got a new DVD-writer.
Today I installed the writer and it got detected witout any real trubble.

Its set as master and my old CD-Writer as slave.

Now, to the problem. When I put a CD/DVD in the tray Ubuntu finds it and mounts it, but when I am done with it and want to take it out, it complains that "the device is bussy" and I dont know what to do.

It seems like it doesnt have a "permanent" moutn point but rahter like a temorary one is created (as with a Memmory stick), that it calls /media/cdrecorder, when I dont have anything in it there is no such mount point.

I realy dont know what to do with it... the CD writer still works fine, but I would like to get this to work to.

Can anyone help me on this?

---

### Post by mlomker on 2005-09-30
You can create a permanent mount point if you want to by adding a line /etc/fstab.  Something like:

```

/dev/hdc        /media/hdc      auto     user,noauto,unhide      0       2

```

I haven't seen the 'busy' error before.  You get that when you give it the eject command?

---

### Post by Kimm on 2005-10-01
Thank you, now it works great.

I named the mount point /media/dvdrom0 to match the CD.

I dont even get the busy error anymore when I try to eject it... pretty strange

---

