---
title: "using terminal for hoary=&gt;breezy"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by jubuntu on 2006-01-10
i saw a terminal script for updating hoary to breezy, though it came with a warning that it was strictly experimental..

does anyone know of a guide that could help me safely do this?

---

### Post by timfrost on 2006-01-10
Basics:
```

# change repositories - this uses perl, but you can edit sources.list
# with any text editor 
sudo perl -pi.bak -e 's/hoary/breezy/' /etc/apt/sources.list

# download the new Packages and Sources files
sudo apt-get update

# and run the upgrade
sudo apt-get dist-upgrade

```

---

