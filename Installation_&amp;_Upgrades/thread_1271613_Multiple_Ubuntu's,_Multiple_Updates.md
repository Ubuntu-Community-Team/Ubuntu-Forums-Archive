---
title: "Multiple Ubuntu's, Multiple Updates"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by sideaway on 2009-09-21
Hey there guys, I have three computers that I own, all three run Ubuntu (one dual boots 7, but that's beside the point) Here in New Zealand we have pretty **** internet tbh, we pay per gig and it's horrendously expensive and it's very slow. So I'm just wondering if there is a way to ultimately update one, and setup the others to fetch their updates from the other, or at least before the computer goes to update/install something, it queries other computers on the network to see if they have the libraries or files necessary? And then if possible automatically retrieve them...

This technology would be awesome. I have a 1000mb network setup as I do a lot of file transfers (me updating a computer at a 1000mb/s would blow my mind...)

Cheers guys, just wondering if this technology exists.

---

### Post by hellmet on 2009-09-21
I know that its possible to setup a local (on your network) central update server on your network that fetches updates from the ubuntu server. Then, your other computers could just download their updates from the local central server. How do you do this? Sorry, I don't know.

---

### Post by Aearenda on 2009-09-21
Try [apt-cacher]("http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher") (that's what I use), or better [apt-cacher-ng]("http://ubuntuforums.org/showthread.php?t=981085") (I'm too lazy to have tried this). There are other ways too, like setting up a full mirror - but the cacher way only fetches what you actually need.

Update - found a [clearer howto]("http://www.ubuntugeek.com/apt-cacher-ng-http-download-proxy-for-software-packages.html") (but it's for Intrepid - all you need to install it now is 'sudo apt-get install apt-cacher-ng') and [user manual]("http://www.unix-ag.uni-kl.de/~bloch/acng/html/index.html") for apt-cacher-ng.

Update: Posting this made me try apt-cacher-ng instead of apt-cacher! It was easy to set up, and it works, so far.

---

### Post by sideaway on 2009-09-21
Thanks guys, will give them a shot :)

---

### Post by Darkwing-Duck on 2009-09-23
Here are a couple more choices for mirroring for a network. Apt-proxy and apt-mirror.

Here is a guide for working with both of them.

[http://gwos.org/udsf/doku.php/core:repository:mirrors](http://gwos.org/udsf/doku.php/core:repository:mirrors)

Hope this points you in the right direction.

---

