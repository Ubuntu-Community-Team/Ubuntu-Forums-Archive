---
title: "Making apt-get recognize a deb file downloaded manually"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by bumpkin on 2009-07-31
I have down loaded several deb files for jaunty and am trying to get the various package managers install it. None will install it as the deb files can not be found. Any way to make synaptic or apt-get recognize this deb file? 

Will  "file-roller -a=<archive>  <filename>.deb " work? 

I don't know what "<archive>" should be for apt-get.

---

### Post by Partyboi2 on 2009-07-31
Hi, could you not use dpkg to install the deb packages?
cd to location of download debs eg
```
cd ~/Desktop
```
```
sudo dpkg -i package
```

---

### Post by spcwingo on 2009-07-31
If you have all the debs in the same directory you could just:

```
cd /path/to/directory
```

followed by:

```
sudo dpkg -i ./*.deb
```

---

### Post by bumpkin on 2009-08-01
dpkg worked.

Thanks!

---

