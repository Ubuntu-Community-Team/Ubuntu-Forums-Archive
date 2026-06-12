---
title: "Own apt-get server"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by Krisken on 2009-09-10
Dear,

I do have some servers of my own, all using ubuntu.  
Just to be curious, is it possible to set up my own apt-get server?  And if so, is there any how-to?

Kris

---

### Post by MJWitter on 2009-09-10
You might like to take a look at apt-cacher-ng.  You can install it on one server and then direct the others to it and it will keep all the packages it downloads, so each will only need to be downloaded once. This is great for saving time and bandwidth.  

[How to]("http://ubuntuforums.org/showthread.php?t=981085"), although it is available in the repository, so you can skip the install part if you prefer.

If you would like the whole repository(something like 50GB of data) I believe there is something called apt-mirror?

---

### Post by i.r.id10t on 2009-09-10
> **MJWitter said:**
> 
If you would like the whole repository(something like 50GB of data) I believe there is something called apt-mirror?

Yes, apt-mirror is what you want, and yes, it takes a good bit of disk space.   I'm mirroring Ubuntu Jaunty and Debian Lenny on a 80gb disk w/ a minimal Debian install to host it all.

---

