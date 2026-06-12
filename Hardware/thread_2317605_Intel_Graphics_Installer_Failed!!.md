---
title: "Intel Graphics Installer *Failed*!!"
date: 2016-03-18
forum: Hardware
---

### Post by eric5912000 on 2016-03-18
Ensuring consistent system... OK
Listing packages... OK
Setting up repositories... OK
Installing packages...
    Updating package cache... Failed

Heres the error popup...


W:Failed to fetch [http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.



I installed the key's in the terminal already, Please help!

---

### Post by Bucky Ball on 2016-03-18
*Thread moved to **Hardware**.*

Welcome. Just wondering why you are installing these drivers. Intel graphics is 99% covered already in the Ubuntu kernel. What is the actual problem that has caused you to investigate third-party PPAs for a solution? 

Please open a terminal and paste this in:

> sudo lshw -C video

Post the output here between code tags (there's a link for how to use them in my signature at bottom of this post).

PS: Best to avoid third-party PPAs where possible. Remember that you use them at your own risk and they have nothing to do with the official Canonical repositories and most of us here can't give you much help when they break apart from confirming that the PPA is broken for us, too.

Also worth noting that if you ever upgrade, you should disable any PPAs you've installed manually, especially for graphics. They can seriously break the upgrade process.

PPS: It looks like the PPA you are trying to install is a Ubuntu-tweak related thing. Ubuntu-tweak has nothing to do with installing graphics drivers and is available for [direct download here]("http://ubuntu-tweak.com/"). I don't use Ubuntu but thought UTweak was already a default app in a standard Ubuntu. :-k

---

### Post by buzzingrobot on 2016-03-18
Unity Tweak Tool is in the repos, but not Ubuntu Tweak. The latter's Github page hasn't seen any substantive changes in a couple of years.

---

### Post by v3.xx on 2016-03-18
Your ppa has not been updated for a couple of years.  No Wily (15.10) release.

[http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/](http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/)

---

