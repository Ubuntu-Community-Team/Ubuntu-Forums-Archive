---
title: "Webserver on a small Notebook"
date: 2006-05-06
forum: Hardware &amp; Laptops
---

### Post by GoodPanos on 2006-05-06
I got this Acer TravelMate 340T with 192MB RAM and 450MHz processor.  Currently I'm running Ubuntu with OpenBox which runs pretty good.  No complaints there.

I wanted though, to install Apache, MySQL and PHP to run osCommerce.  Do you think the Notebook is going to handle it?  Is there any tweeks I can do to make the NB run smoother?

Any suggestions are appreciated.

---

### Post by hw-tph on 2006-05-07
It should prove no problem unless you're going to run osCommerce on it as a production server. :)

I have had several laptops acting as small servers. Most have had busted screens or other problems making them unsuitable for regular use. The disks, especially in older notebooks, are really slow, and that will show if they are under load and need to swap. Also, since the disks are slow chances are database access won't be too snappy.

My latest laptop server was a 366MHz Thinkpad 600E with 192MB RAM. I had added a faster 5400rpm (8MB cache) 40GB disk to it previously and it greatly improved performance.

If you're using Ubuntu you should do a server install. No need for graphical environment so skip X altogether. It just makes things more complicated. And if the battery still works you have a built-in UPS. :)

Håkan

---

### Post by paritybit on 2006-05-07
Are you trying to run a development enviroment on your laptop?
I do this a bit to play around with things.. I recommend tweaking apache and mysql to reduce their memory usage.
I configure them to only fork 1 or 2 processes as I don't have anyone else using it so I don't need to worry about server load. This saves a little bit of memory.
If you are planning to run a production server, as has already been pointed out this probably isn't a good idea, but it would definately run.

---

### Post by GoodPanos on 2006-05-08
Thank you for all your replies.

Did I mention it's a Pentium III 450MHz?

> Are you trying to run a development enviroment on your laptop?  Yes, I am.  I just want to be able to work on my website when out on the road and sync up the changes with my real server (another notebook but way more powerful :D ).

> I recommend tweaking apache and mysql to reduce their memory usage.  I configure them to only fork 1 or 2 processes as I don't have anyone else using it so I don't need to worry about server load. This saves a little bit of memory.  Any directions on how to do that is greatly appreciated.

---

### Post by GoodPanos on 2006-05-09
Any hints on the above?  I would really like to get this going.

Thanks

---

### Post by paritybit on 2006-05-10
Well it really depends on the apache version. Try looking at apache.org and look at the documentation. There is a lot of help there.
As for mysql just change the cache values in the my.cnf.

I am being a bit non-specific as I just dodgied my config and it seems to work but may not be 'the right way'(tm)

---

### Post by hw-tph on 2006-05-10
If you're not a big fan of preforking I suggest you have a look at [lighttpd](http://www.lighttpd.net). It is small, very easy to configure and secure. I use it on my main laptop as development platform, and if someone asked me to ship a web server now I would most certainly chose lighttpd.

It is not available as a package in Ubuntu, but it is not difficult to build from source. And like I said, configuration is very easy. Just remember to build php with at least --enable-fastcgi --enable-force-cgi-redirect enabled (otherwise it won't work with lighttpd). No --with-apxs since you should build for lighttpd, not Apache.


Håkan

---

### Post by GoodPanos on 2006-05-12
What about osCommerce, will it run on lighttpd?

Care to write a how to in the HOWTO's section?

---

### Post by hw-tph on 2006-05-12
osCommerce runs on pretty much any web server with PHP support, with PHP as module (Apache) or CGI. I have never used osCommerce but after browsing the documentation I am confident it will work with lighttpd.

I started on a lighttpd howto some time ago but now I guess I'll have to finish it too. :)


Håkan

---

