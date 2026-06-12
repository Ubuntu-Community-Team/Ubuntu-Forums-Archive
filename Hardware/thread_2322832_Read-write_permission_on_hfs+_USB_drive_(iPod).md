---
title: "Read-write permission on hfs+ USB drive (iPod)"
date: 2016-04-30
forum: Hardware
---

### Post by Michael_OSullivan on 2016-04-30
I'm having trouble writing to a HFS+ formatted iPod nano (3G). Linux (and Banshee) can read it fine but the Properties show the owner as Root with User (me!) and Others having only read access.

I've edited the fstab to contain an entry for the iPod's UUID:

```
UUID=<iPod's UUID>    /media/iPod      hfsplus    force,rw,user,noauto     0    0
```

From what I can figure out, that should give r/w access to the user and bypass any journalling problem, but it isn't allowing me to write (& hence let Banshee sync files).

Unfortunately, the 3G iPod nano is one that can't be reformatted to FAT32 or something more obliging than HFS+.

Any suggestions?

---

### Post by yancek on 2016-04-30
The official Ubuntu documentation at the link below.

[https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

Do you have hfsprogs installed?

[http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write](http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write)

---

### Post by Michael_OSullivan on 2016-05-04
Thanks for your help. Looks like I'll have to get onto a Mac to shut off journalling and to check the Mac UID.

To battle!

---

### Post by Michael_OSullivan on 2016-05-08
> **yancek said:**
> The official Ubuntu documentation at the link below.

[https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

Do you have hfsprogs installed?

[http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write](http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write)

... and I think we have a solution!

I simply logged in as su and used chown to change the ownership to myself (and the group 'users'):

```
chown -R michael:users /media/iPod
```

Then, rather than using chmod to adjust read/write permissions, I simply used the Properties dialog box in the Nemo file app to re-set them. Banshee is now able to sync the iPod, and they all lived happily ever after...

Many thanks for your help!

M.

---

