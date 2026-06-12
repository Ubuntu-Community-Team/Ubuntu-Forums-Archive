---
title: "Need to partition 250 gig HD..fdisk? cfdisk? parted?"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by bpont on 2006-04-30
What do Ubuntu users recommend for paritioning and formatting very large hard drives?

---

### Post by pappo on 2006-04-30
I use GParted.  It works great.  Of course this assumes you are using Gnome desktop.

---

### Post by [S|G] on 2006-05-01
[QUOTE=pappo]I use GParted.  It works great.  Of course this assumes you are using Gnome desktop.[/QUOTE]
Well, you can use gparted on kde as well. If you installed kubuntu and doesn't have it, open a terminal and type:
```

sudo apt-get install gparted

```

---

### Post by iball on 2006-05-01
I have always used cfdisk.

I don't think it is installed by default, you will probably need to install it using "sudo apt-get install cfdisk".  Ultimately, use whatever you feel comfortable with, they all have the same function, and will give the same end result.

--Ian

---

### Post by az on 2006-05-01
Large or small, parted does all the partitioning.

You may need to install ntfstools if you want to create or shrink an ntfs partition.

---

