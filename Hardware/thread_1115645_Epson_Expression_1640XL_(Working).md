---
title: "Epson Expression 1640XL (Working)"
date: 2009-04-04
forum: Hardware
---

### Post by joewski on 2009-04-04
I am pleased to announce I have found a a solution "Epson Expression 1640XL scanner" under jaunty 9.04. When I first tested this scanner it wasn't recognised by ubuntu at all. My research showed that nobody had tested or managed to get this scanner to work under ubuntu successfully to date.

After some digging around I was able to locate the necessary files to install.  [Epson Linux drivers page (LINK)]("http://ubuntuforums.org/newthread.php?do=newthread&f=332")

After downloading iscan_2.18.0-2_i386.deb I found one depency missing when I tried to install iscan. Requiring libltdl3_x.x.xx-x_xxxx.deb as well. These are not in the ubuntu repositories when I searched.

Fortunately I was able to find at the [debian site (link)]("http://packages.debian.org/squeeze/libltdl3") the required library package.

I choose libltdl3_1.5.26-4_i386.deb from the debian lenny distro because I had done a lot of research and read of people having trouble in the past getting this scanner to work with any distro of linux. 

Anyway it seems like the library file did the trick. I don't know if I really needed iscan_2.18.... because I tested every other scanner application in linux and found them all to work.

I have attached the i386 deb packages to this post but if your using another process you will need to look on the link I have provided.

---

