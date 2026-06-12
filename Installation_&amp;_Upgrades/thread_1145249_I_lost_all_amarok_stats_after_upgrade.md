---
title: "I lost all amarok stats after upgrade"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by nandelbosc on 2009-05-01
Hi to all! ;)

Yesterday I decided to upgrade the version of 8.10 to 9.04, everything went well except amarok. 

when I started amarok (amarok 2, before the update had 1.4) I began to cry when I see that I have no statistics, after over two years collecting them!

How can recover it?

If helps I have a copy of amarok folder before update.

Thank's!

---

### Post by fermulator on 2009-05-03
Same problem here!

Not only that, but where did all the advanced amarok settings go?

I had a MySQL database setup for increased performance ... don't see any way to reconfigure it to use MySQL...

---

### Post by fermulator on 2009-05-03
> **fermulator said:**
> Same problem here!

Not only that, but where did all the advanced amarok settings go?

I had a MySQL database setup for increased performance ... don't see any way to reconfigure it to use MySQL...

OH:  Figured it out.  It's because Amarok2 uses by default an embeded MySQL database.  In amarok14, I had it configured to use a localhost MySQL 'real' database.  All playlists, settings, etc., were stored in the DB.

I don't think Amarok 2.0.2 is quite ready for primetime.  I've downgraded back to 1.4 for now until A2 is more polished.

[http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/](http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/)

---

### Post by nandelbosc on 2009-05-06
I downgraded to amarok 1.4 too.

[http://littlergirl.googlepages.com/DowngradePackages.html](http://littlergirl.googlepages.com/DowngradePackages.html)

or ([http://ubuntuforums.org/archive/index.php/t-1122517.html](http://ubuntuforums.org/archive/index.php/t-1122517.html))...

```
to downgrade:
first and get rid of amarok2 and any tracks it left behind!
Code:

sudo aptitude purge amarok

then you should find .deb packages of previous version somewhere:

Code:

apt main cache : /var/cache/apt/archives
OR
apt-cacher cache : /var/cache/apt-cacher/packages
OR
found them in intrepid repository over the net, search here : "http://packages.ubuntu.com/"(don't forget to set distribution to intrepid in search page)

then you need to install them by hand (just double click on it ) with this order :
Code:

amarok-engine-xine_1.4.10-0ubuntu3_i386.deb
libgpod3_0.6.0-5ubuntu2_i386.deb
amarok-common_1.4.10-0ubuntu3_all.deb
amarok_1.4.10-0ubuntu3_i386.deb

use this order to satisfy dependencies AND ignore warnings about newer version available in software channels during installation of packages

now run amarok 1.4! if it works good you should hold it to prevent package mangers from upgarding it:
Code:

sudo aptitude hold amarok
```

I think Amarok 2 is not ready for general use... we need to wait

---

### Post by .nedberg on 2009-05-06
I see you have downgraded to Amarok 1.4, but I'll post this anyway.

I just found a way to import the old Amarok 1.4 stats into Amarok 2. It is buildt into Amarok 2.

Settings->Configure Amarok, Collection tab, Import Collection.

It will let you import everything from Amarok 1.4.

I have not tested it though!

---

### Post by dubhear on 2009-05-06
Hi! Have you tried to update cellection yet?

run amarok > settings > configure amarok > collection 

make the path right? 
                      works in verion 1.49

---

### Post by apswartz on 2009-05-08
Seems to import songs, but NOT playlists!!! :(

---

### Post by DaveQB on 2009-06-03
Thanks for that. Shame about the playlists part though.

---

