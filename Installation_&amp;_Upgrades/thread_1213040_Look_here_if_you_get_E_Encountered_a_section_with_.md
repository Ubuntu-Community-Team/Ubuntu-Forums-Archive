---
title: "Look here if you get E: Encountered a section with no Package: header E: Problem with"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by zintinio on 2009-07-14
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

If you are not comfortable in the terminal, just type in 
~$ gksu nautilus
It will open nautilus. From there navigate to /var/lib/dpkg
Then you will see a few files that say status, status old, and status-bad. Delete them all. Then right click, and create a new Document. Rename it status. Your package manager will now work again.

---

### Post by Partyboi2 on 2009-07-15
You should be able to replace your existing status file with the old one without having to delete everything :)
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broke
sudo cp /var/lib/dpkg/status.old /var/lib/dpkg/status
```

---

### Post by zintinio on 2009-07-15
If it works...:KS

---

### Post by chriswcy on 2009-08-25
You can try following commands:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

