---
title: "Build a network storage server"
date: 2005-05-31
forum: Hardware &amp; Laptops
---

### Post by momo66 on 2005-05-31
With all the cheap hard drives out there for sale (Compusa has a 160Gig for $30 after rebates this week), I've decided to build  a network storage server with about a terabyte of disk space.  On it I will store my DVD collection (about 150 movies) and about 500 CDs that I have ripped. Dont worry,  I'm old enough to have purchased all of these before bit-torrent came about.

Anyway I would like any ideas on the best way to configure this server and storage using Ubuntu.  I will have roughly 5 drives of various sizes- about a terabyte total.  I also would like to be able to expand to more drives in the future.  Also would like any feedback on cases, motherboards, and CPU.

I read somewhere that LVM file system was good for serving large files such as videos and that ext3 was better for smaller files.

thanks for any help you can give,

Mike

---

### Post by thrift on 2005-05-31
A solution that I use and that you may find to be a decent one is to use EVMS with the RAID 5 plug in.  I use 3 200G on two IDE controllers.

In this way you get plenty of speed(I get around 80MB/s off of 3 drivers), you get fault tolerance(one disk can die and it's no big deal.  you'll also find that mdadm will email you if the S.M.A.R.T. information on your drive reports a problem), and you'll get the ability to easily add more disk to your RAID set later.

It's a little tricky to get rolling, but once it's up it's pretty sturdy.  If the machine were to die or anything Ubuntu is pretty good about autodetecting EVMS volumes, so that is really helpfull.

LVM/EVMS are not file systems.  You will need to format the volume with a filesystem.  In my experience

Ext2 is very fast, but offers no filesystem tolerance.
Ext3 is well rounded, not particularly fast, and offers the best stability/reliability.
ReiserFS can really move around small files fast, and has options that can save you a bit of space.
XFS can push around big files very fast, but I have had some reliability problems with it in the past when it was just being merged with the Linux kernel.  These issues are probably gone now, but I'd check into it.

I currently use Ext3 in my setup.

Your biggest issue may actually be your IDE controllers here.  Make sure you get well supported IDE controllers, ie not Highpoint(I had a hell of a time with them and their IDE cards)

Hope this helps and Good Luck.

---

### Post by momo66 on 2005-06-01
Thanks for all the useful tips.

---

### Post by tom-ubuntu on 2005-06-01
Have a look at the Terastation from Buffalo Technology:
[http://www.buffalo-technology.com/products/storage.php](http://www.buffalo-technology.com/products/storage.php)

Such a thing is exactly what I need in the future: No as power consuming as a whole computer, small, Raid5, webinterface, runs linux. What else do you need?  :)

---

### Post by thrift on 2005-06-01
[QUOTE=joeuser]Have a look at the Terastation from Buffalo Technology:
[http://www.buffalo-technology.com/products/storage.php](http://www.buffalo-technology.com/products/storage.php)

Such a thing is exactly what I need in the future: No as power consuming as a whole computer, small, Raid5, webinterface, runs linux. What else do you need?  :)[/QUOTE]

Affordability?
Ability to add harddrives later?
It's really not that small...
A Linux computer could be configured to do a lot more for a lot less.
Not very configurable.
If part of it breaks good luck fixing it.

Advertising certain products is not what Ubuntu is about.  If you have an honestly good idea on how someone can do what they are trying to do then that's great, but throwing out links to products is just annoying.

---

### Post by tom-ubuntu on 2005-06-03
Sorry, was no intention to advertise this product. Just saw it in a magacin and I was pretty excited about it. If you don't like it, ok. I do. Just wanted to share it with others who are looking for a storage server....

---

