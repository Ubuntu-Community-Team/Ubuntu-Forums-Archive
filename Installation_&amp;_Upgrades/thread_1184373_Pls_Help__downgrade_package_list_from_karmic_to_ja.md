---
title: "Pls Help : downgrade package list from karmic to jaunty"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by jagdishrao on 2009-06-11
Hello all

Pls help me
i have ubuntu server 9.04 jaunty 64 bit installed on one of my local test server
Yesterday night i did a 
do-release-upgrade -d 
to just check for any new releases and it found karmic kaola alpha1 release
i cancelled the downloading of upgrade files as i wasn't intrested in upgrading and just want to check.

but problem is since then when i do
sudo apt-get update
the server hits the karmic repositories and shows me 384 upgrades to be done

pls help how do i revert back my repositories to jaunty jackalope completely

will replacing all the karmic to jaunty in the sources.list
work?

i already read this [Downgradehowto Guide]("https://help.ubuntu.com/community/DowngradeHowto")
but its for the case where upgrade has been done
i have not yet downloaded and upgraded karmic.just my packages has been updated and i want to revrt my
package list back to jaunty


pls guide


yesterday i

---

### Post by Partyboi2 on 2009-06-11
Hi, since you have not downloaded and installed any karmic packages you should be able to replace karmic with jaunty in your sources.list.

---

