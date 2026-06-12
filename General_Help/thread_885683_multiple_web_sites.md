---
title: "multiple web sites"
date: 2008-08-10
forum: General Help
---

### Post by mcai8sh4 on 2008-08-10
Greetings!

After using xubuntu for a couple of months without any real problems, I've decieded to set up a little home server. In less than 3 hrs I had installed xubuntu, set file sharing, ssh, ftp, LAMP.
On my web server I'm playing with gallery2.
For general server admin I'm using webmin.

To access my website I've setup no-ip to forward to port 80 on my ip adress.

My question... If I want to run two (or more) websites (again going through no-ip) how will apache know which to go to. If anyone has seen a tut on how to do this please let me know.

On another note, thanks to everyone who has posted questions/answers in Ubuntu forums, common problems are no longer problems thanks to you guys (and gals :) )

---

### Post by spiderbatdad on 2008-08-10
apache has a virtual hosts file /etc/apache2/sites-available
you can access multiple sites by pointing apache to the sites under the directory options, so by using your ipaddress/site1 or  ipaddress/site2 you would bring up the index.html, or whatever, in either or those folders. Instead of ipaddress, of course, you could use a dynamic server name.

---

### Post by mcai8sh4 on 2008-08-10
Ah, I see. So I can ignore the no-ip bit.
I had mysite.com/site1 and mysite.com/site2 but both had the same parent dir. This way I access them the same, but they're held in different locations on the disk.

I'll have a play around, see what happens. Thanks

---

### Post by mcai8sh4 on 2008-08-11
Sorry about this folkes, but I still didn't get it. I've found more info (via google) but when I access my server I always get the default.

I'll keep trying, hopfully I'm just missing somthing simple.

If anyone finds a simple tut, please post - it may be one I haven't trawlled though.

Thanks again.

---

### Post by steve-82 on 2009-07-13
i have the same issue, did u manage to resolve this?

---

