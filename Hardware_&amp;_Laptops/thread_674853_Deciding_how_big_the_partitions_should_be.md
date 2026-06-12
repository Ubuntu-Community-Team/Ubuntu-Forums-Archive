---
title: "Deciding how big the partitions should be"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by murmel on 2008-01-22
Hello everybody! I'm working with an older server and have just bought a new hard drive. The two things I need help with is
[list="1"]How big should the partitions be? The new hard drive is 160GB and the old one is 20GB. I don't think I should use the same percentage on the new one as I have on the old one.
How big should each of the partitions be?[/list] 

[list="2"]When copying the data from one drive to another I use "dd if=/dev/hda1 of=/dev/hdb1". But is there any directories I shouldn't copy? Maybe /proc and others? How do I exclude those when copying?[/list]

Thanks!

- Simon

---

### Post by az on 2008-01-22
> **murmel said:**
> Hello everybody! I'm working with an older server and have just bought a new hard drive. The two things I need help with is
How big should the partitions be? The new hard drive is 160GB and the old one is 20GB. I don't think I should use the same percentage on the new one as I have on the old one.
How big should each of the partitions be?

That depends on your needs.  What kind of server is it?  What do you use it for.  Who uses it?  What do you need separate partitions for?


> **murmel said:**
> 
When copying the data from one drive to another I use "dd if=/dev/hda1 of=/dev/hdb1". But is there any directories I shouldn't copy? Maybe /proc and others? How do I exclude those when copying?

Thanks!


dd copies an entire filesystem.  You can't select folders and individual files.  You shouldn't copy the filesystem you are running using dd.  If you want to dd one partition to another, do it from a live cd.

Once you dd the filesystem over to the other drive, you are going to need to grow the filesystem to expand it to the rest of the new (bigger) partition.

---

### Post by murmel on 2008-01-22
Allright. I'm going to use it as fileserver and ldapserver.

---

