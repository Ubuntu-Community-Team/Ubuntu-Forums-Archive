---
title: "Backport Howto for grsync in Hardy Heron."
date: 2008-11-05
forum: General Help
---

### Post by albinootje on 2008-11-05
Backport Howto for grsync in Hardy Heron.

I tried grsync in Hardy Heron, and noticed that it segfaults after you add a new session. 
I found a bug-report about it, where people mentioned that this problem is resolved in the grsync version in Intrepid Ibex.

* First add the Intrepid Ibex deb-src lines to /etc/apt/sources.list :

Here's an example of *just* the universe deb-src lines,
make sure you add all of the deb-src you might need! :

deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) intrepid-updates universe

* sudo apt-get update

We need a newer version of debhelper to be able to create the newer grsync backport-package

* sudo apt-get install -t intrepid debhelper
* sudo apt-get -b source debhelper

After the compiling is successful :

* sudo dpkg -i debhelper*deb

Start with the dependencies and build of grsync itself :

* sudo apt-get build-dep grsync
* sudo apt-get -b source grsync

And after successful compilation :

* sudo dpkg -i grsync*deb

Start grsync and check the version-number, it should be 0.6.1 instead of 0.6 :p

Backporting is cool! 

But for more "complicated" applications it can be much more difficult than in this example. Don't start backporting everything! 

HTH

---

