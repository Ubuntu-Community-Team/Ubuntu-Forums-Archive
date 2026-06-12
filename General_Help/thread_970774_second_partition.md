---
title: "second partition"
date: 2008-11-04
forum: General Help
---

### Post by bimmer jake on 2008-11-04
i recently switched back to ubuntu from kubuntu and in doing so i creaded a second partition for ubuntu as to not loose my files.  i reformatted the old partition and now i can't use it.  it says inaccessible.  i'm using ubuntu 8.1 and gparted.  it says it's partitioned and formatted but i can't use the partition.

what am i doing wrong?

---

### Post by akshar_patel_47 on 2008-11-04
Mount the partition... by right clicking on the partition and than mount.

Edit : You'll have to mount using Gparted and not just simple mounting..

---

### Post by bimmer jake on 2008-11-04
It is mounted.  i wish it was that simple.  i can't copy any files to it or even create a new folder.

---

### Post by logos34 on 2008-11-04
you may have to chown or chmod it:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(bottom)

---

### Post by akshar_patel_47 on 2008-11-04
or type in the terminal

```
sudo nautilus
```

go to the drive

in it's properties go to permissions and than select your name in the list of owner.

Now you can do what ever you want in that drive. As simple as that.

---

### Post by bimmer jake on 2008-11-04
> **logos34 said:**
> you may have to chown or chmod it:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(bottom)

That took care of it.  thank a ton!

---

