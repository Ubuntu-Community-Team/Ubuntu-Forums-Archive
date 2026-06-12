---
title: "Wireless Security on Eee PC 901"
date: 2009-04-13
forum: Hardware
---

### Post by jackyboy633 on 2009-04-13
Hi

I'm using a Ralink RT2860 on my Eee PC 901 running Ubuntu 9.04 (Jaunty Jackalope). I love it, but my only gripe is that I cannot get my wireless to work with it. My security is WPA2-PSK TKIP. I've tried switching to AES encryption, but it affects other wireless devices in my home. I have also tried ndiswrapper, but still no success. I need my wireless, so any help would be greatly appreciated.

Thanks,
Jack (jackyboy633)

---

### Post by loza on 2009-05-15
i'm having same problem too!

---

### Post by enpark on 2009-05-21
As do I.

---

### Post by Phil Urich on 2009-05-23
The [Debian Wiki mentions this](http://wiki.debian.org/DebianEeePC/Model/901).  Also there seems to be a post on these very forums about [the patch](http://ubuntuforums.org/showthread.php?t=1145941), but once again Jaunty using 2.6.28 has us a bit in the dark; so, it sounds like it's fixed already in 2.6.29, but of course that isn't in Jaunty nor even is it released yet. The issue seems to be a regression in the RaLink drivers, and the solution (for now) seems to be downgrading to the previous version.

There's a bug report submitted [over at launchpad](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/339891), and there's a post outlining the exact fix here: [http://ubuntuforums.org/showpost.php?p=7022855&postcount=13](http://ubuntuforums.org/showpost.php?p=7022855&postcount=13)

---

