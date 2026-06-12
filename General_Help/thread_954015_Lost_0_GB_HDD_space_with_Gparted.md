---
title: "Lost 0 GB HDD space with Gparted"
date: 2008-10-20
forum: General Help
---

### Post by Jeztastic on 2008-10-20
Hi,

I have uninstalled Ubuntu from my laptop, and deleted the partitions it was on. I then expanded /C to the maximum allowed (all in Gparted). I now only have 111 GB of HDD space showing, but it's a 120 GB drive. What gives?

Thanks!

---

### Post by shawnrgr on 2008-10-20
Please search the forums before posting

[http://ubuntuforums.org/showpost.php?p=2645327&postcount=2](http://ubuntuforums.org/showpost.php?p=2645327&postcount=2)

---

### Post by DGortze380 on 2008-10-20
> **Jeztastic said:**
> Hi,

I have uninstalled Ubuntu from my laptop, and deleted the partitions it was on. I then expanded /C to the maximum allowed (all in Gparted). I now only have 111 GB of HDD space showing, but it's a 120 GB drive. What gives?

Thanks!

That's about normal for a 120GB drive. My 120GB WD has 111.7GB free when formatted to HFS+, FAT32, NTFS, or EXT3.

---

### Post by Jeztastic on 2008-10-21
> **shawnrgr said:**
> Please search the forums before posting

[http://ubuntuforums.org/showpost.php?p=2645327&postcount=2](http://ubuntuforums.org/showpost.php?p=2645327&postcount=2)

Please think before you click send. I did search the forums, and there was nothing applicable to my query. The post you linked to was of no help to me, as I already stated, my drive is formatted to NTFS. If I am missing something, please explain it to me, as I welcome **constructive** comments. How rude.

Edit: OK, I can see how you could mis-read my post - I did not explicitly state it was NTFS. Still...

---

### Post by Jeztastic on 2008-10-21
> **DGortze380 said:**
> That's about normal for a 120GB drive. My 120GB WD has 111.7GB free when formatted to HFS+, FAT32, NTFS, or EXT3.

Thanks. Grr. Lying Toshiba!

---

### Post by geirha on 2008-10-21
Harddrive manufacturers use units of 1000 when listing capacity, so 120GB is approximately 120000000000 bytes, but operating systems likes to use units of 1024, so 120GB will be displayed: 120000000000/1024/1024/1024 = 111.76 GiB

See these for more info.

[http://en.wikipedia.org/wiki/Binary_prefix#Hard_disk_drives](http://en.wikipedia.org/wiki/Binary_prefix#Hard_disk_drives)
[http://xkcd.com/394/](http://xkcd.com/394/)

---

### Post by /////// on 2008-10-21
When your computer calculates gigabytes it does it in the standard which says that 1024 bytes = 1 kb 1024kb = 1 mb 1024mb = 1gb
When a hard drive is advertised, the amount they give you is actually 120 000 000 000 bytes, so following the convention that the computer uses to measure space, 120 000 000 000 / 1024 / 1024 / 1024 gives you ~111.758708954gbs

edit: lol woops only saw geira's post after I posted...

---

