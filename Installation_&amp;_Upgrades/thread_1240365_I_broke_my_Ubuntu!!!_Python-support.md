---
title: "I broke my Ubuntu!!! Python-support"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by fryser_d on 2009-08-14
Ok... I was try the install the new new version on Deluge(BitTorrentClient) and the 1.1.9 required the python-support_0.90 witch I didn't have at the time. :(

So I downloaded the file:
python-support_0.90.0_all.deb

And well... ****** up my ubuntu... my widgets won't appear, and the .deb installer don't work anymore. So I downgraded by force

```
sudo dpkg  -i python-support_0.8.4_all.deb
```

And now... nothing :guitar:

even when I reboot I don't see any changes.

Help! :-({|=

---

### Post by cariboo on 2009-08-14
You may need to completely remove python-support_0.90.0_all.deb, open a terminal and type:

```
sudo apt-get purge python-support_0.90.0_all
```

---

### Post by fryser_d on 2009-08-14
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package python-support_0.90.0_all
```

But I solved the problem by

Synaptic> update python-support

:guitar:

Thx anyways for your time.

---

