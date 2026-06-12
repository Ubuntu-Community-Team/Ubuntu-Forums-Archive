---
title: "messed up Fat32 partition, lost everything?"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by Nils-Johan on 2005-09-02
Okej, my brain needs some serious neural surgey... 
I got a standard error mez after a panic shutdown but when i was about to correct it i messed up....insteed of doing 
[CENTER]```
dosfsck /dev/hda2
```[/CENTER]
i did 
[CENTER]```
mke2fs /dev/hda2
```[/CENTER]
and f**k up complete.....
My intuitive theory is that i *just* wrote over the information file in the partition becourse when i used nautilus some files from a early stage in partitions life emerged. I am not sure but my hope is to that faint idea that all i have to do is rewrite the first file with the information that it once had. 
Ideas? Comments?

---

### Post by dbrine on 2005-09-04
you can try this guide. it discusses hdd with data already there and new hdd's.

[http://www.linuxplanet.com/linuxplanet/tutorials/4232/1/](http://www.linuxplanet.com/linuxplanet/tutorials/4232/1/)

---

