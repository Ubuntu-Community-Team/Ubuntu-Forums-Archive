---
title: "Installing Ubuntu 9.04 on an external hdd"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by mgoostinflower on 2009-06-18
Hello,
I am trying to install ubuntu on my external hard drive (I have Windows xp on my very small 16gb internal hard drive).

I partitioned my external hard drive as follows:
/dev/sdb3 ntfs 7.81mb (this is where I installed Grub)
/dev/sdb1 ntfs 212.38gb (this is where all of my documents are)
/dev/sdb2 extended partition 20.49gb
    - /dev/sdb6 ext4 18.63gb (this is where I installed jaunty)
    - /dev/sdb5 linux swap 1.86gb

The install went fine. All of the files are there and in their appropriate place. I can still boot xp when I don't boot from usb. 

But I still cannot boot ubuntu from usb. When I try to, Grub has "Error 17", which I guess means it can't find Ubuntu? I'm not sure what I need to do to fix this...perhaps editing my menu.lst file somehow? 

Any help is appreciated. And I am new to Ubuntu, so please try to be explicit about command lines and such. Thanks!

---

