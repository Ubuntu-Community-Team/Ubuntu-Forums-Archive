---
title: "HELP!! - Is my Hard Drive Dead?"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by hammer v2 on 2007-11-09
HELP! Ubuntu is not booting properly!!! I'm getting this big scary message. Anyone got any Idea how to fix it?

FSCK DIED WITH AN EXIT STATUS 4



Help!!!! :(


H.

---

### Post by chrischris349 on 2007-11-09
Looks like your Ubuntu install is corrupted mate, Reinstall

---

### Post by Steve1961 on 2007-11-09
Boot from the live cd and try running fsck manually

---

### Post by az on 2007-11-09
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

Find another computer, obtain another hard disk and use the above tool to make an image of your partition(s).

Using gnu-ddrescue, you may be able to read through any errors on your disk and save your data.  You have a high chance of recovering all your data that way.

Stop using the disk.  Do not write to it (do not try to fix errors)  Just image it.

Keep the drive as cool as you can during the process.  It would take a few hours (depending on the size and what kind of hardware it is.  When reading through errors, it can take days.

---

