---
title: "Can we do Spanned HDDs?"
date: 2009-09-24
forum: Hardware
---

### Post by doas777 on 2009-09-24
howdy all,

I have a number of  hard disks that I share to my network (via samba) off my file server with share names like Files1, Files2, Files3, DifferantFiles1, Differantfiles2, etc.
the reason for the numbered shares is that no drive i possess is capacious to hold all the content.

In some OSs there is a means to treat several physical disks as a single volume. is that possible in ubuntu (assuming that the disks cannot be reformatted/repartitioned)?

failing that, is there any way I can make samba present a set of folder shares as a single share?

Thanks folks!

---

### Post by doas777 on 2009-09-25
bump bumpity bump bump

---

### Post by louieb on 2009-09-25
Haven't used it in years. But lvm (logical volume management) is what your looking for. 

Unless things have changed you'll have to unload your data, build the lvm volume, and put the data back. But then again found this [https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

---

### Post by doas777 on 2009-09-25
thanks! 
I saw a little about lvm in my initial look, but I am afraid it won;t work for me (at least not now).  i have no concerns about rebuilding the OS, but i can't back up the data at present, but i think i will look into converting my disks to lvm2 one TB at a time. your link implied that it was possible (even desirable) though it did not say how.

I'm also going to expirement with sharing a folder of symlinks to see if i can at least get each catagory accessible from one share. no idea how samba will treat links, but is worth a quick expiriment.

thanks again!

---

