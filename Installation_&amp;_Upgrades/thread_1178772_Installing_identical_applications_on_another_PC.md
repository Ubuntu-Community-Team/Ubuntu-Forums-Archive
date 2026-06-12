---
title: "Installing identical applications on another PC"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by blues2use on 2009-06-04
I have seen several versions of this method and am wondering if I use the commands listed, will I be able to install the same applications I have under Wubi 9.04 on my laptop to a new desktop PC I just bought. I plan to run XP SP 3 and Wubi 9.04 on the new desktop.

From the terminal:

    dpkg --get-selections > apps.txt

then save this file to a USB stick

Now, copy the file to my new desktop's 9.04 Desktop and from terminal:

    dpkg --set-selections < apps.txt
    dselect update
    apt-get dselect-upgrade show

Is this the proper method or should I bite the bullet and install all of apps one-at-a-time on the new desktop under Wubi 9.04?

Thanks for the help

---

### Post by blues2use on 2009-06-05
Bump

---

