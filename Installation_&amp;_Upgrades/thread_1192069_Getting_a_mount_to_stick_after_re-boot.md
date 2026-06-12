---
title: "Getting a mount to stick after re-boot"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by suchin on 2009-06-19
Why don't my new slave drive mount stick? It is an ext3 and I have in 9.04 done:

sudo mkdir sdb1
sudo mount /dev/sdb1 /media/sdb1
sudo nano /etc/fstab /dev/sdb1 /media/sdb1 ext3 defaults 0 0

It mounts, the file dir is there. Drive shows up in orange? Works fine but is gone after re-boot? Code wrong?

In the Media property box I have this line:
Mount Option: rw errors=continue data=ordered
that mean anything?

Suchin

---

### Post by Cheule on 2009-06-20
Hi there,

I just had the same problem as you recently, take a look at [my thread on the subject and read through carefully.]("http://ubuntuforums.org/showthread.php?t=1188343")

Hopefully there will be something in there that will help you. :)

---

