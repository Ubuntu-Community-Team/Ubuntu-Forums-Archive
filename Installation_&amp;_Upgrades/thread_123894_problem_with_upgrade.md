---
title: "problem with upgrade"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by matawang on 2006-01-31
pls help me to upgrade to breezy. i tried to change the word "hoary" to "breezy" in file apt/sources.list. however, the file is "read-only". what should i do....
pls help:-k

---

### Post by Gcool on 2006-01-31
That's indeed the way to go. But keep in mind that you have to edit it as root.

sudo nano /etc/apt/sources.list

---

### Post by byen on 2006-01-31
or for a graphical text editor....
sudo gedit /etc/apt/sources.list ;-)

---

### Post by matawang on 2006-02-01
hi again,
thanks for the help. yes i managed to upgrade to breezy.

---

### Post by geekphreak on 2006-02-01
For future distribution version upgrades, test [update-manager]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-January/014700.html")

---

