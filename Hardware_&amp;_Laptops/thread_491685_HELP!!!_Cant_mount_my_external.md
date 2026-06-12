---
title: "HELP!!! Cant mount my external"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by Orion2014 on 2007-07-03
I tried converting it from an NTFS to an ext3 and here is the error im getting now...

[[IMG]http://img117.imageshack.us/img117/4828/screenshot2xy4.th.png[/IMG]](http://img117.imageshack.us/my.php?image=screenshot2xy4.png)

Please help, I have data on here i need to retrieve. 

Thank you for your help.

---

### Post by jusmurph on 2007-07-04
What do you mean by Converting?

---

### Post by ugm6hr on 2007-07-04
> **Orion2014 said:**
> I tried converting it from an NTFS to an ext3 and here is the error im getting now...

I don't think it is possible to *convert* file systems (i.e NTFS to ext2/3) without formatting the HD (i.e. you will have wiped the data).
> Please help, I have data on here i need to retrieve. 
:(

---

### Post by Orion2014 on 2007-07-04
Ok well I have most of the data backed up onto DVD's. Is there any way I can format this thing so ubuntu can use it?

---

### Post by ugm6hr on 2007-07-04
> **Orion2014 said:**
> Ok well I have most of the data backed up onto DVD's. Is there any way I can format this thing so ubuntu can use it?
Yes.  Probably safest to use fat32 file format if sharing between Windows and Ubuntu (assuming you don't need to store any files larger than 4GB).

So just format it in Windows - and select Fat32 as file format.  Give it a Volume Name while you're at it, and it will then automount as /media/*VolumeName* in Ubuntu.

If you want to format in Ubuntu - best done with GParted.

---

