---
title: "Need help finding a backup solution for home server"
date: 2008-10-16
forum: General Help
---

### Post by flatland2d on 2008-10-16
I have over 100GB of pictures I've taken over the last five years (when I first got a digital camera).  I am building a home server that will act as a file server for my home network and allow me to VPN and remote desktop from outside.  My goal is to come up with a viable backup solution for protecting my pictures on this server.

Initially I was thinking setting up RAID 1 on the server dedicated just to pictures (OS and others on separate drive).  Then I started reading about how RAID isn't such a good idea, and that what I really need is a backup and not always on reliability.

I'm leaning towards manually cloning my pictures drive (probably going to be 1TB) to an external drive of the same size.  I would do this once a month or so.  It won't always be up to date, but I could stand to lose pictures from a few weeks ago instead of many years worth of pictures.  Another option would be automating this process and keep the backup drive internal to the server, but I'd be sacrificing the physical security from having the backup stored elsewhere.  I could maybe live with that.

What are everyone's thoughts on this?  What would be a good program to use for the cloning?  Optical storage is kind of out of the question because I really don't want to take the time to burn 100+GB of DVD's, but I may end up doing that slowly over time.  What's the long term reliability of DVD's anyway?  Don't the degrade (or is that just in light)?

Thanks a bunch for any help/advice you can give.

---

### Post by hyper_ch on 2008-10-17
I use a NSLU2 (with a custom debian on it) and have attached 2x 1 TB drives to it. As it is a debian system I made it so that it can passwordless login (with a keyfile) to my computer and rsync the data... I do that every night and using the power of hardlinks to create snapshot-style backups back for 90 days.

---

### Post by ilrudie on 2008-10-17
Look into [Bacula]("http://www.bacula.org/en/").  I have a friend who runs his own development hosting for about 5 or 6 people and he has nothing but great things to say about Bacula.

---

### Post by amac777 on 2008-10-17
rsnapshot is pretty good as well. I use it to keep weekly, monthly, and yearly backups automatically. (it uses rsync so only needs to copy files that change, and it uses hard links so that files that don't change only need to be stored once.)

---

