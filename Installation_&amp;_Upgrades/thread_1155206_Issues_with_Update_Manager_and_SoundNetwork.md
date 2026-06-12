---
title: "Issues with Update Manager and Sound/Network"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by creideiki on 2009-05-10
Well, I'm a new user of Ubuntu, I'm still using 8.04, and I recently upgraded from one kernel variant to a newer one. Problem is, my system killed my sound drivers (not a good thing when you're using the compy as an audio rig!) and my network interfaces are now... well who the hell knows where they are, but it can't see them.

So I went into the older kernel variant (which has - yay - sound and network) to upgrade the system again (and to get some drivers and other updates for my programs). Only issue now is, power outage and the system died mid-update. Now, I still have the sound and network issue, and now I can't even run the update manager!

Can any one help?

---

### Post by Partyboi2 on 2009-05-11
Hi, boot into your old kernel and open a terminal (Applications>Accessories>Terminal) and type
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```If any error out post the output.

---

