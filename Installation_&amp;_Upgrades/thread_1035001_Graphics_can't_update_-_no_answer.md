---
title: "Graphics can't update - no answer"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by dougalkerr on 2009-01-09
I am still having problems trying to update my graphics card. The updates are available as I am getting notification but as a few others are finding I am getting this message when I try to install the updates:

W: Failed to fetch [http://ppa.launchpad.net/compiz/ubuntu/pool/main/c/compizconfig-settings-manager/compizconfig-settings-manager_0.7.8-0ubuntu3_all.deb](http://ppa.launchpad.net/compiz/ubuntu/pool/main/c/compizconfig-settings-manager/compizconfig-settings-manager_0.7.8-0ubuntu3_all.deb)
  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (113 No route to host)

This happens with anything I am trying to install/update not just the graphics drivers and I haven't seen a successful answer posted yet.
I have even replied to one post that was asking for a copy of my 'sources.lst' file but didn't get a second reply after that so it makes me wander if anyone has an answer.
I did solve it temporarily by reinstalling a fresh copy of Ubuntu 8.10 after reformatting my hard drive but, this is a bit drastic and it only lasted a couple of days.
If anyone has any ideas I am sure a lot of people would be very grateful. I know I will be as it is holding up my whole experience with Ubuntu 8.10 - it doesn't happen with previous versions, 6.06, 7.10, 8.04.
Thanks.

---

### Post by gettinoriginal on 2009-01-09
Looks to me like you do not have the appropriate "third party software" enabled in your Software Sources.  Try this:
Run these two in terminal, one at a time:

```
 sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list 
```

```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update 
```

---

