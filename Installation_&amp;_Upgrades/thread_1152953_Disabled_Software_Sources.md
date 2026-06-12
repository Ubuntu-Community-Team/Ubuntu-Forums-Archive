---
title: "Disabled Software Sources"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by GNUway Tech on 2009-05-08
On my upgrade to Jaunty, some of my Third-Party Software sources were disabled. How do I enable them again??????

Also, my Adept Updater keeps telling me that it has blocked updates. Would that be because of the disabled sources, or can I get them otherwise?????

---

### Post by taurus on 2009-05-08
From a terminal, edit your /etc/apt/sources.list and remove the # in front of the repo you want.

```
sudo nano -Bw /etc/apt/sources.list
```
After you're done editing it, save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

