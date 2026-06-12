---
title: "Unable to Download Plugins"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by confusedmatt on 2009-10-31
Hi all,

Just upgraded from 9.04 to 9.10 and the basics seem to work, but when I try to get Firefox to play flash it tells me I need a plugin.  When I try to do this I get the following message:


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-date-time1.38.0_1.38.0-6ubuntu6_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-date-time1.38.0_1.38.0-6ubuntu6_i386.deb)
  Could not connect to gb.archive.ubuntu.com:80 (42.1.4.80), connection timed out


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-thread1.38.0_1.38.0-6ubuntu6_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-thread1.38.0_1.38.0-6ubuntu6_i386.deb)
  Unable to connect to gb.archive.ubuntu.com http:


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gnash/gnash-common_0.8.6-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gnash/gnash-common_0.8.6-0ubuntu1_i386.deb)
  Unable to connect to gb.archive.ubuntu.com http:


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gnash/gnash_0.8.6-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gnash/gnash_0.8.6-0ubuntu1_i386.deb)
  Unable to connect to gb.archive.ubuntu.com http:


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gnash/mozilla-plugin-gnash_0.8.6-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gnash/mozilla-plugin-gnash_0.8.6-0ubuntu1_i386.deb)
  Unable to connect to gb.archive.ubuntu.com http:

I get similar problems with Update Manager and Evolution Mail.

And advise, much appreciated,

Matt

---

### Post by nrondou on 2009-10-31
same problem here, only I did a fresh install of Ubuntu 9.10 and I use the belgian servers

edit: found the solution myself: go to System> Administration> Software sources
in the ubuntu-software tab choose an other server to download from (e.g. the main server)
this makes it work for me!

grtz

---

### Post by confusedmatt on 2009-10-31
Ok, so having read some of the other issues I altered my network connections so that IPV4 method is Automatic (DHCP) and now I can download plugins and update manager works.

But Evolution still wont receive any mail.

Now it's stopped again!

---

### Post by goodindian on 2010-06-18
> **nrondou said:**
> same problem here, only I did a fresh install of Ubuntu 9.10 and I use the belgian servers

edit: found the solution myself: go to System> Administration> Software sources
in the ubuntu-software tab choose an other server to download from (e.g. the main server)
this makes it work for me!

grtz
Thanks dude. :)
it worked for me as well...

---

