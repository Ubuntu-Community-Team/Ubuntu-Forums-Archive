---
title: "i have problem with google earth installization"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by panagiotaros on 2009-10-09
hellow...can somebody tell me how to fix a problem with my pc???? 
it can't install google earth because it can't open googleearth.bin...
what can i do???

---

### Post by Partyboi2 on 2009-10-10
Hi, to install Googleearth open a terminal (Applications>Accessories>Terminal) and change directory to where the downloaded googleearth.bin file is. So if it is on your Desktop
```
cd ~/Desktop
```
then make the bin file executable with
```
chmod +x GoogleEarthLinux.bin
```
then install by typing
```
sudo ./GoogleEarthLinux.bin
```

---

