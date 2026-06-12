---
title: "need to upgrade php 5.2.4 to 2.9"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by ridinglowest on 2009-05-28
I am using turnkey linux(lamp) which is ubuntu just command line and a web gui. Bear with me I am a web developer not a linux guru. 

I normally use xampp as a testing server which I guess emulates a linux server on a windows machine, but what is nice is the php version is up to date has every extension possible already setup. 

with ubuntu I have firgured out how to update and install new libaries but something is still not right. In comparing the phpinfo file on the turnkey with the one on xampp, they look pretty close except for version numbers.

Is there a way to update all of apache or php5 to latest and greatest and with all extensions (ex curl, pdf, gd etc)

I tried.. apt-get update
apt-get install php5 and it seemed to work but the php into file still says 5.24-2 when xampp says 5.29

what am I doing wrong?

---

### Post by lemming465 on 2009-05-30
Which version of Ubuntu are you using?  Last months' 9.04 "jaunty jackalope" has PHP 5.2.6; if you really need 5.2.9 and don't want to compile it yourself you probably need to be running Debian "sid" (experimental), not Ubuntu.  The way the Ubuntu release cycle works will always put it 6-8 months behind the bleeding edge.

---

### Post by zonezero on 2009-05-31
So what your telling everyone is that Ubuntu will only update the repositories on the release cycles even when were talking about security holes open in something as common as PHP?

OpenBSD and FreeBSD both update the ports tree and the binary packages when there are security fixes and new versions of things like PHP and certainly not on a 6 month release schedule.  They don't even make you run the "experimental" version of the OS!

My Ubuntu desktop install has always had many updates for various bits of software that is installed including security fixes, but never looked too closely.  Perhaps I should look and not assume that security is a priority instead of release schedules.

---

### Post by lemming465 on 2009-05-31
No, no, no.  Security fixes will be backported promptly.  New features will wait for the next release.  This is the standard behavior of all reputable Linux distributions, as well as the *BSD's.  Commericial software also tends to wait new features on new releases, except that many vendors don't patch promptly, and unlike free software new releases tend to be very erratic. The exceptions, for people willing to tolerate breakage, are things like Debian "sid" which deliberate roll in new versions continuously; but they don't promise that the pieces play nicely with each other.

To figure out if a specific security fix you are interested in has been backported, you'll have to check the series of [ubuntu security notices]("http://www.ubuntu.com/usn") for the packages in question, just like you'd have to do with the upstream project.  There is a web site, a mailing list, and an RSS feed, so it's not hard to track these if you are interested.  The most recent PHP patch is [USN-761]("http://www.ubuntu.com/usn/USN-761-2") from April 27th which fixes CVE-2008-5814 and CVE-2009-1271.

Most desktop people just run *update-manager* and figure they don't have too many worries; folks with servers have to be slightly more paranoid.

There is a reason that when you install an Ubuntu box there are a bunch of updates pending; these are the ongoing stream of security and bug fixes getting caught up to current.

---

