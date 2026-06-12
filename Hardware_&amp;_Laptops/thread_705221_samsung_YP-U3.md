---
title: "samsung YP-U3"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by rob1984 on 2008-02-23
hi,

i'm trying to mount my samsung YP-U3 so that i can drag and drop files onto it.

windows will let me do this but ubuntu doesnt automount the device. 
since all my mp3s are on my ubuntu partition and windows cant read ext3 this is a bit of a pain.

ive tried mounting sda1 but i get
```
mount: special device /dev/sda1 does not exist
```

i'm pretty new to this so i dont know where to go from here.

any help is greatly appreciated.

---

### Post by HunterThomson on 2008-03-22
I also have a YP-U3.... BUT i am also new to Linux.... Have you found out a way to transfer files? I was reading about the YP-U3 wen I got it a year ago and Windows uses a driver that is alredy in the windowsOS maby if we found the name of the driver we could download it and use like ndswrapper to make the driver work for Linux.... What do you think? :idea:

---

### Post by HunterThomson on 2008-04-14
I have found a fix....

sudo apt-get install gnomad2

That will do it :guitar:

---

