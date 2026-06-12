---
title: "Tor package missing?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by sygin on 2009-04-24
Hi,

I am trying to install Tor, but I can not find the package in the Ubuntu Jaunty Universe repositories.

Am I missing something?

Thanks,
Sygin

---

### Post by lotuseclat79 on 2009-04-27
Hi sygin,

It looks like a Tor package has not yet been built for Jaunty to date.  It is available for Intrepid, however.  Neither is Vidalia yet available for Jaunty.

You can get the latest sources for Tor at: [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor)

Look for tor-0.2.1.14-rc.tar.gz and download to your Desktop: ~ubuntu/Desktop

The build instructions are (assuming you have gcc/g++ installed + dependent libraries - try to download the intrepid tor .deb package and inspect the control file for its dependencies):
sudo apt-get install libevent
tar zxvf tor-0.2.1.14-rc.tar.gz
cd tor-0.2.1.14-rc
./configure
make
sudo make install

Check out Tor documentation for configuration information at: [https://www.torproject.org/docs/tor-doc-unix](https://www.torproject.org/docs/tor-doc-unix)

-- Tom

---

### Post by sygin on 2009-04-27
Thanks for the info.

Cheers,
Sygin

---

### Post by geimapi on 2009-05-03
I got it working by using these instructions:
[https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian](https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian)

I just wrote "jaunty" as the distribution and followed the "Verifying signatures with apt 0.6.x" instructions as well.

---

