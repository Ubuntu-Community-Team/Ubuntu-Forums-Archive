---
title: "Installing downloaded file"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by don Ladd on 2009-03-28
trying to figure out how to install OOo_3.0.1_LinuxIntel_en_US_deb.tar.gz. Have had no success installing this downloaded file. Any instruction would be helpful

---

### Post by Partyboi2 on 2009-03-28
Open a terminal (Applications>Accessories>Terminal) and change to where the downloaded file is, so if it is on your Desktop type
```
cd ~/Desktop
```then extract it
```
tar xvzf OOo_3.0.1_LinuxIntel_en_US_deb.tar.gz
```then you need to change into the new directory that was created
```
cd OOO300_m15_native_*/DEBS/
```then install with
```
sudo dpkg -i *.deb
```

---

