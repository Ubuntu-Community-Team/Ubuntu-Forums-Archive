---
title: "Update Open-Office Error"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by Friend5545 on 2009-07-01
I was trying to update my ubuntu today with all of the necessary updates and i got this error.

> E: /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb: failed in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: failed in buffer_write(fd) (10, ret=-1) 
Does anyone know how I can fix this?
thanks in advance.

---

### Post by aquavitae on 2009-07-01
I might be wrong, but it looks like its having trouble downloading some of the files; specifically, writing them to disk. Try again and see if it works. Otherwise... any signs of hard drive failure?

---

### Post by Friend5545 on 2009-07-03
That's all that I can find but since I can't update I can't install certain programs, so i can't really test it out.

---

### Post by Friend5545 on 2009-07-03
And I did try reinstalling it but it gives me the same error every time. Should I just skip over this part of the update?

---

### Post by aquavitae on 2009-07-04
I don't really know what the problem is, but since it can't write to the files, it suggests one of three things:
[LIST=1]
[*]You're out of disk space.  You can check it with ```
df -h
```
[*]The files already exist, but are set to read only. You should be able to see this with ```
ls -l /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb
```
[*]Your hard drive is failing. This is quite complicated to check because you have to unmount it first. If you think this is the problem, do a bit of research into fsck and badblocks, and if you get stuck checking it, post back.  But there are probably a few good howtos around if you google it.
[/LIST]

---

### Post by Friend5545 on 2009-07-04
ok thanks for your replying I will try these methods out!

---

### Post by Friend5545 on 2009-07-05
uhh with the second one what am i supposed to see if it is set to read only?

---

