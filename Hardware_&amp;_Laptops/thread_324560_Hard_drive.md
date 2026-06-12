---
title: "Hard drive"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by ockertom on 2006-12-23
Hi peeps how are you? Just installed 6.06 and I like this a lot, looks like windows is a past thing, well not exactly lol.
The problem I am having is I have a 320gb wd, I went into disk management disabled it, ten placed it in /media/hdb1. as the main drive is in /dev/hdb1, I then went to a term and used sudo chown "me" /media/hdb1 thats seemed to work, then went an did a chmod 777, that seemed to work, well it didnt lol cant access the disk, it does have a nt partition on it, do I need to perform some othe bloody thing? 

Been a while since I done this :)

Thanks for any advice in advance

---

### Post by taurus on 2006-12-23
You cannot change permissions for ntfs or vfat.  It has to be set in /etc/fstab...  Here's a guide for you to look at!

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

