---
title: "[SOLVED] errror while installing"
date: 2008-10-11
forum: General Help
---

### Post by suhaib1thariq on 2008-10-11
my downloading was interrupted due to power failure...after that my installation showed error...
```
sudo dpkg --configure -a
```
i was instructed to do the above code ...but i still got error when i try to install and uninstall what can i do

E: /var/cache/apt/archives/pavucontrol_0.9.5-1ubuntu1_i386.deb: files list file for package `mplayer-skins' is missing final newline



how can i solve this

---

### Post by overdrank on 2008-10-11
> **suhaib1thariq said:**
> my downloading was interrupted due to power failure...after that my installation showed error...
```
sudo dpkg --configure -a
```
i was instructed to do the above code ...but i still got error when i try to install and uninstall what can i do

E: /var/cache/apt/archives/pavucontrol_0.9.5-1ubuntu1_i386.deb: files list file for package `mplayer-skins' is missing final newline



how can i solve this

Hi and have you tried ```
sudo apt-get install -f
```

---

### Post by iponeverything on 2008-10-11
> **suhaib1thariq said:**
> my downloading was interrupted due to power failure...after that my installation showed error...
```
sudo dpkg --configure -a
```
i was instructed to do the above code ...but i still got error when i try to install and uninstall what can i do

E: /var/cache/apt/archives/pavucontrol_0.9.5-1ubuntu1_i386.deb: files list file for package `mplayer-skins' is missing final newline

how can i solve this

Should be easy to fix:

```
mv /var/lib/dpkg/info/mplayer-skins.list /root

```

---

### Post by suhaib1thariq on 2008-10-11
thanks...its now installing

---

