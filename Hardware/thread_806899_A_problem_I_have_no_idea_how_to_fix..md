---
title: "A problem I have no idea how to fix."
date: 2008-05-25
forum: Hardware
---

### Post by enephs on 2008-05-25
Ok, so basically I've partition my hard drive so that I have 30gigs on ubuntu and 30 on Windows. For the past few days I've been super board so I downloaded tons of games and software. What can I do to clean up my hard drive and find all the old folders left behind from games and such?

---

### Post by bwhite82 on 2008-05-25
Assuming you've installed everything through Synaptic, you can uninstall them there. Remnants can be found in your home folder. Make sure to select "show hidden files" in Nautilus.

---

### Post by chewearn on 2008-05-25
```
sudo apt-get autoremove && sudo apt-get clean
```

Will clean out unused and archived packages.

---

