---
title: "How can I completely remove Amarok 2 and downgrade to old version?"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by Pathofcinders on 2009-04-11
Hi everybody, this is my very first post here :)

I'm having a problem: I upgraded to Amarok 2 (in Ubuntu) but I just don't like it and want to come back to the older version (the one in add/remove applications). I tried to uninstall Amarok 2 with "sudo apt-get remove" but it doesn't work, Amarok is always there. Any suggestions?

In order to install it I had previously enabled this repository in the sources.list file: [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main.

I'm still a newbie and unexperienced with Ubuntu so please be patient :P

---

### Post by Pablo Pablovski on 2009-04-11
I did just that the other day, following the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=1084971&highlight=remove+amarok&page=8](http://ubuntuforums.org/showthread.php?t=1084971&highlight=remove+amarok&page=8)

You can uninstlal 2.0 from Synaptic. 

You need to edit your sources.list to include Bogdan's PPA repository, which contains the old version of Amarok 1.4, before you can install it from Synaptic. It explains how to do that in the thread, but post back if you're unsure.

---

### Post by p2000000000 on 2009-04-26
after upgrading to jaunty i found amarok2 is installed and i didn't liked it too, many features gone, many bugs appeared, why?! :D

to downgrade:
first  and get rid of amarok2 and any tracks it left behind!
```
sudo aptitude purge amarok
```
then you should find .deb packages of previous version somewhere:

```
apt main cache : /var/cache/apt/archives
OR
apt-cacher cache : /var/cache/apt-cacher/packages
OR
found them in intrepid repository over the net, search here : "http://packages.ubuntu.com/"(don't forget to set distribution to intrepid in search page)

```
then you need to install them by hand (just double click on it :D) with this order :
```
amarok-engine-xine_1.4.10-0ubuntu3_i386.deb
libgpod3_0.6.0-5ubuntu2_i386.deb
amarok-common_1.4.10-0ubuntu3_all.deb
amarok_1.4.10-0ubuntu3_i386.deb

```
use this order to satisfy dependencies AND ignore warnings about newer version available in software channels during installation of packages

now run amarok 1.4! if it works good you should hold it to prevent package mangers from upgarding it:
```
sudo aptitude hold amarok
```
unfortunately update-manager don't respect aptitude's holding mechanism, DON'T use update-manager it will upgrade to amarok2 :( 
use "sudo aptitude full-upgrade" instead
hope amarok2 will get better sooner!

---

