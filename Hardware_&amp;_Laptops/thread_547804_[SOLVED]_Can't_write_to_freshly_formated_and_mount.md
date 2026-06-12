---
title: "[SOLVED] Can't write to freshly formated and mounted ext3 partition..."
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by diablo75 on 2007-09-10
I used this guide:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

And I have the drive mounted as /media/40gig

I can open the drive, and I can see a lost+found folder, but I can't write to it.  What's up?

---

### Post by diablo75 on 2007-09-10
Never mind....I just looked at the link I posted up again and realized I stopped a little early.  oops

---

### Post by ashwin108 on 2008-06-03
I'm having this problem, please help me.

---

### Post by sisco311 on 2008-06-03
> **ashwin108 said:**
> I'm having this problem, please help me.

Change the owner of the partition.
Open a terminal (Applications -> Accessories -> Terminal) and type:
```
sudo chown -R $USERNAME. */media/mount-point*
```Replace */media/mount-point* with the actually  mount point of the partition.

---

