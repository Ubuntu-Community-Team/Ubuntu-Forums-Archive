---
title: "INstalling Amarok 2.0"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by Dobbie03 on 2009-01-10
Has anyone got any links or a walk through on how to do it?

---

### Post by Partyboi2 on 2009-01-10
if you are using intrepid (8.10) you can add[B]
```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
```[/B]to your sources.list
From a terminal (Applications>Accessories>Terminal) ```
gksu gedit /etc/apt/sources.list
``` then add the above repo and save. Then back in the terminal
```
sudo apt-get update
sudo apt-get install amarok-kde4
```

---

### Post by Dobbie03 on 2009-01-10
Thanks for your help, all sorted now :)

---

