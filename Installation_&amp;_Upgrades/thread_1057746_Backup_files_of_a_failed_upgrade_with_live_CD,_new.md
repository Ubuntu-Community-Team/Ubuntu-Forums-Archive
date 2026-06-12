---
title: "Backup files of a failed upgrade with live CD, newbie"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by elpix on 2009-02-02
I tried to do an upgrade from 7.10 to 8.04 without success.
I want to backup some files, the partition is visible with live cd, but they are locked, cant even read them. It says I need the permissions.
I reda about nautilus but doesn t seem to do a lot ( opens a file browser with only the live cd files.)
Can anybody help, the files I cant get are my baby daughters pictures!
Thank you

---

### Post by Pumalite on 2009-02-02
Do it with:
```
gksudo nautilus
```

---

### Post by elpix on 2009-02-02
Pumalite,
Thank you for responding.
I am trying 

gksudo nautilus

But it opens what I think is nautilus (resembles a file browser), but the two locations are
root for the live CD, and
desktop for live CD also

cant even get to 
disk
where my data is an that can be seen in a & non Nautilus) file browser.

---

### Post by Pumalite on 2009-02-02
Tell me where is your data (which partition). Post:
```
sudo fdisk -lu
```

---

