---
title: "Internal Error, Could not perform immediate configuration (2) on libc6"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by GDent on 2009-03-16
last week i came across this error, like hitting a wall with mach 10, while performing a dist-upgrade from gutsy to intrepid.

after serious investigations i learned, that this was caused by apt due to cyclic dependencies. or what ever this is called... :)
I recognized it would be useful to post the information on ubuntuforums!

the one and only solution i found, is following this:

```

sudo apt-get remove libc6-dev
sudo apt-get -d install libc6
cd /var/cache/apt/archives
sudo dpkg --force-depends --install libc6_2.8~20080505-0ubuntu7_i386.deb findutils_4.4.0-2ubuntu3_i386.deb
sudo apt-get -f install
sudo apt-get dist-upgrade

```
(adapt .deb packages to your needs)
i suggest not to apply, ```
sudo apt-get clean
```as suggested on
[http://www.x47.dk/2009/01/ubuntu-server-6-8.html](http://www.x47.dk/2009/01/ubuntu-server-6-8.html)
because this wipes your /var/cache/apt/archives, and on slow connections you seriously won't! that after collecting ~700MB packages.

---

### Post by taurus on 2009-03-16
I don't think you can jump or skip a release.  You should have gone from gutsy -> hardy -> intrepid.

---

### Post by GDent on 2009-03-16
dist-upgrade is working atm... i am eager to experience the result.
luckily, this box is not vital, so why stop an experiment? :)

i am going to publish any error reports here. if no problem arises, then all went ok.

after a third ubuntuuser confirms the solution, i view above code as a working way to untie the interdependencies between libc6 and findutils.

---

### Post by ssaidwho on 2009-03-27
Following upgrade instructions at 

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I got this error while running

sudo apt-get install update-manager-core

The first apt-get install command failed for me with the same error, but I went ahead to installing the debian package (in other words, started with line 3) and got update-manager-core installed.

Thanks!

---

