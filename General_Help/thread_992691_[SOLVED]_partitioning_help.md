---
title: "[SOLVED] partitioning help"
date: 2008-11-25
forum: General Help
---

### Post by banana jama on 2008-11-25
can anyone tell me what what those keys mean next to the drive names and how i can get rid of them. im using ubuntu 8.10 and the program is called Gnome Partition Editor. i think i attached the picture in this post i don't know how to show screen shots. 

/home/akeem/Desktop/Screenshot--dev-sda - GParted.png

---

### Post by ndefontenay on 2008-11-25
I'm not sure but I think that it means you will need root access to write on those.

It means you'll have to use gksudo gedit filename whenever you want to work with anything located there.

If that is the case, I wouldn't change that.

I suppose you are not blocked in anyway while using ubuntu, so it's not major.

---

### Post by banana jama on 2008-11-25
i want to expand the ubuntu hard partition how do it. your're right im not blocked in ubuntu in anyway

---

### Post by logos34 on 2008-11-25
to expand the ubuntu partition(s) you have to unmount / and /swap, then the extended partition itself (sda3), but you can only do that using Gparted on the ubuntu live cd or a live rescue/utility cd.  Root cannot be mounted when resizing.  You can, however, move the ntfs partition over to free up more space.

---

### Post by CatKiller on 2008-11-25
Those partitions are mounted - you're running it from your normal install, aren't you? You can't change a partition that's mounted (hence displaying them as locked) and you can't unmount your / partition while you're using it.

As logos34 says, the solution is to boot from a live cd so that you have access to the programs you need without having to run them from your / partition.

Most live cds will automatically mount your swap partition to improve performance. If you're going to change your swap partition in any way - such as by moving it out of the way to expand your other partitions - then you'll need to unmount it again. You can do this with the command ```
sudo swapoff -a
```

---

### Post by banana jama on 2008-11-25
thanks

---

