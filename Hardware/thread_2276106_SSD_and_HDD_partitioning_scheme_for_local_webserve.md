---
title: "SSD and HDD partitioning scheme for local webserver running ubuntu 14.04 LTS"
date: 2015-04-30
forum: Hardware
---

### Post by nikhil12 on 2015-04-30
I have 1 SSD of 128GB and 1 HDD of 1TB.

I am setting up a web server running Nginx PHP to be run on a local network to be accessed by 5 - 10 people at a time.

What should be the Partitioning scheme for HDD and SSD? all of the threads are targeted for gaming and personal use desktops.
On my server there will be no movies, no heavy applications like Games.

Having / on SSd is a no-brainer, but what about /swap /home etc.

Also, my main concern is, Should I have the www directory of Nginx on SSD, each website can be up to 250MB so maybe in future I might end up consuming all the SSD.

---

### Post by TheFu on 2015-04-30
I would put everything on the SSD until you outgrow it.  Then move what needs to move to the spinning disk - if not an entire mount point, just subdirs and uses symlinks.

---

