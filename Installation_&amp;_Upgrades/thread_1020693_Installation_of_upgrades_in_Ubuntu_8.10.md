---
title: "Installation of upgrades in Ubuntu 8.10"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by kaemran on 2008-12-24
Hi All,
Whenever i try to install any upgrade in UBuntu 8.10 i get the following error and cant install any update,


E: /var/cache/apt/archives/libbonobo2-common_2.24.0-0ubuntu1_all.deb: files list file for package `base-files' is missing final newline

Can any one please help me in this regard. Thanks

---

### Post by Partyboi2 on 2008-12-24
Open a terminal (Applications>Accessories>Terminal) and type
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/base-files.list

``` 
then 
```
sudo apt-get update && sudo apt-get upgrade
```

---

