---
title: "where do update files go?"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by tacoma50 on 2009-03-26
After instaling 8.10, I ran update manager and it installed 256 updates. 

Where do the update files get downloaded to?
Are they deleted automaticly after they are installed? If not can I delete them?

---

### Post by 505 on 2009-03-26
The are downloaded to /var/cache/apt/archive The best way to delete them is by running the command 'sudo aptitide clean'

---

### Post by damis648 on 2009-03-26
They are not cleaned right away, to clean them up:
```
sudo apt-get clean
```
and if you want to remove unneeded dependencies,
```
sudo apt-get autoremove
```

---

