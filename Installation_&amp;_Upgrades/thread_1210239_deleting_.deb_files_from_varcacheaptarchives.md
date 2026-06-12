---
title: "deleting .deb files from /var/cache/apt/archives/"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by g03t3098 on 2009-07-11
what would happen if i deleted the .deb files from /var/cache/apt/archives/. I'm using ubuntu remix if that makes a difference (don't see why...)
 
i recently went on a downloading spree on my eeepc and since i have limited storage space (and need to free up as much space as possible) i was wondering if (deleting)/(moving to flash stick) the stored .deb files would have nasty effects on my system.
 
while i don't see any problems doing this since the .deb files just install packages i'm a newbie to linux so i'm loath to do anything that will break my sexy new OS.

---

### Post by drs305 on 2009-07-11
Nothing bad will happen by removing the cache .debs. In fact, there is a command for doing just that:
```
sudo apt-get clean
```

There are also the *autoclean* & *autoremove* commands. Read exactly what the commands do by reading the *man* page, which gives good explanations for the options.
```
man apt-get
```

---

### Post by g03t3098 on 2009-07-12
Excellent. Many thanks.

---

