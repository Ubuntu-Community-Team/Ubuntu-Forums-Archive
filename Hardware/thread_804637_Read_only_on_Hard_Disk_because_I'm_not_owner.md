---
title: "Read only on Hard Disk because I'm not owner ?"
date: 2008-05-23
forum: Hardware
---

### Post by Zeerots on 2008-05-23
I can't write to my second empty HD. In Nautilius I can see the contents, lost&found, but properties says Root is the owner. 

What I did:
I've put a 300gb NTFS SATA harddisk in my PC.
With "Partition Editor" I deleted all partitions, created 1 new large partition and formatted it as ext3.

- How to use this disk fully ?
- Why did the formatting only take 4 minutes ?

Thanks !

---

### Post by mannheim on 2008-05-23
It's normal for a new disk to be set up so that root is the owner (and four minutes isn't surprising either).

To make yourself the owner, make sure the hard disk is mounted, then open a Terminal and type something like:

```

sudo chown [COLOR="Blue"]john:john[/COLOR] [COLOR="Blue"] /media/the-disk[/COLOR]

```

changing the items in blue to match your own situation (your username, and the directory where your drive is mounted).

Don't make yourself the owner unless you're not going to store anything except your own data there. A more flexible approach is to make a subdirectory called "john" or whatever, and make yourself the owner of that.

---

### Post by Zeerots on 2008-05-24
It worked. Thanks a lot, Mannheim.

I was however very surprised not to be able to find this solution on the web myself after 3 hours of searching. 

See my sugestion at Partition Editor: [http://gparted-forum.surf4.info/viewtopic.php?id=1418](http://gparted-forum.surf4.info/viewtopic.php?id=1418) .

Johan Zeerots

---

