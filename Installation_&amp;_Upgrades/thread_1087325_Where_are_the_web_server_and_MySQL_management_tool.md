---
title: "Where are the web server and MySQL management tools?"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by josephmo on 2009-03-04
Using the package installer, I installed the web server, as well as the MySQL server. It said that it installed them successfully (I think). So, I type [http://localhost](http://localhost) and I get the following message:

Not Found

The requested URL / was not found on this server.
Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.0 Server at localhost Port 80

I re-installed. Same results. I cannot find the web server and the MySQL management tool (dashboard, etc.) on any of the menus. What am I doing wrong. Incidentally, when I install PHP or Perl, should I see a category (something like Programming Languages?)

Regards,
Joseph

---

### Post by cariboo on 2009-03-05
The first thing you should do is make sure that apache2 is running. Open an Applications-->Accessories-->Terminal and type:

```
ps ax | grep apache
```

if apache2 is running you should get a result like this:

```
ps ax | grep  apache
16374 ?        Ss     0:04 /usr/sbin/apache2 -k start
21955 ?        S      0:00 /usr/sbin/apache2 -k start
21956 ?        S      0:00 /usr/sbin/apache2 -k start
21957 ?        S      0:00 /usr/sbin/apache2 -k start
21958 ?        S      0:00 /usr/sbin/apache2 -k start
21959 ?        S      0:00 /usr/sbin/apache2 -k start
30332 pts/0    S+     0:00 grep apache
```

There are a  couple of gui/web tools to administer apache2, rapache, it is available in the repositories, but the last time I looked at it, I wasn't to impressed. I would suggest [webmin]("http://webmin.com/") to administer apache2 and the rest of the server and phpmyadmin, which is available in the repositories, to administer mysql. 

One other thing I would suggest it to check the [Server Platform]("http://ubuntuforums.org/forumdisplay.php?f=339") forum, as there is a lot of good information there.

Jim

---

### Post by lykwydchykyn on 2009-03-05
I'll second the recommendation for webmin.  I find it very helpful.

Something must not be right with your configuration, typically you should just get a page that says "It works!"  after installing apache.

What all packages did you install?

---

### Post by josephmo on 2009-03-05
> **cariboo907 said:**
> The first thing you should do is make sure that apache2 is running. Open an Applications-->Accessories-->Terminal and type:

```
ps ax | grep apache
```

if apache2 is running you should get a result like this:

```
ps ax | grep  apache
16374 ?        Ss     0:04 /usr/sbin/apache2 -k start
21955 ?        S      0:00 /usr/sbin/apache2 -k start
21956 ?        S      0:00 /usr/sbin/apache2 -k start
21957 ?        S      0:00 /usr/sbin/apache2 -k start
21958 ?        S      0:00 /usr/sbin/apache2 -k start
21959 ?        S      0:00 /usr/sbin/apache2 -k start
30332 pts/0    S+     0:00 grep apache
```

There are a  couple of gui/web tools to administer apache2, rapache, it is available in the repositories, but the last time I looked at it, I wasn't to impressed. I would suggest [webmin]("http://webmin.com/") to administer apache2 and the rest of the server and phpmyadmin, which is available in the repositories, to administer mysql. 

One other thing I would suggest it to check the [Server Platform]("http://ubuntuforums.org/forumdisplay.php?f=339") forum, as there is a lot of good information there.

Jim

The Apache server is running, but giving me an error message indicating it did not like [http://localhost](http://localhost) (the error message I got when I did [http://localhost](http://localhost) was the following "Not Found The requested URL / was not found on this server.Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.0 Server at localhost Port 80")

so, somehow the configuration for the default page got screwed up. I will try webmin and see if I have any luck with it.
and I did get the

---

### Post by josephmo on 2009-03-05
> **lykwydchykyn said:**
> I'll second the recommendation for webmin.  I find it very helpful.

Something must not be right with your configuration, typically you should just get a page that says "It works!"  after installing apache.

What all packages did you install?

I installed webmin, and it looks pretty full featured. It responded to the following [https://joseph-ubuntu:10000](https://joseph-ubuntu:10000)

I guess I need to play around with it for a bit to figure my way around, and figure out where I can go to change the default domain name (it's not [http://joseph-ubuntu](http://joseph-ubuntu)).

---

