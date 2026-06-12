---
title: "Mirror selection in preseed"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by skylar on 2009-11-01
I'm trying to preseed an Ubuntu 9.04 Desktop install. I think I've gotten everything working, except for mirror selection. No matter what I do I can't get it to use anything except the default Ubuntu mirror. Here's what I have for mirror selection in preseed:

d-i mirror/country string US
d-i mirror/http/hostname string ubuntu.osuosl.org
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string [http://lothlorien:3128](http://lothlorien:3128)
d-i mirror/http/mirror select ubuntu.osuosl.org

I know at least some of these options are being processed because I'm hitting my proxy server. I've turned on debug-ubiquiry and here's what I see in /var/log/installer/debug:

Nov  1 22:04:42 debconf (filter): <-- GET mirror/http/mirror
debconf (developer): <-- GET mirror/http/mirror
debconf (developer): --> 1 us.archive.ubuntu.com
Nov  1 22:04:42 debconf (filter): <-- SET mirror/http/hostname us.archive.ubuntu.com
debconf (developer): <-- SET mirror/http/hostname us.archive.ubuntu.com
debconf (developer): --> 0 value set

I'll be preseeding about 160 laptops in a couple weeks at SC09 and I'd like to play nice with Ubuntu's mirrors. :)

Thanks in advance for any help!

Skylar

---

