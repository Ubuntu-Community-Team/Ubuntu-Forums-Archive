---
title: "Help:E: Wow, you exceeded the number of versions this APT is capable of."
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by jokerqiang on 2009-10-14
Hi,
I got following error with package manager, please help

tiger@tiger-laptop:~$ sudo apt-get autoclean
Reading package lists... Error!
E: Wow, you exceeded the number of versions this APT is capable of.
E: Problem with MergeList /var/lib/apt/lists/ftp.tw.debian.org_debian_dists_lenny_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by Partyboi2 on 2009-10-14
Hi, open a terminal and remove that list with
```
sudo rm /var/lib/apt/lists/ftp.tw.debian.org_debian_dists_lenny_main_binary-i386_Packages
```then re-fetch it with
```
sudo apt-get update
```

Also, sometimes adding debian repos to your sources.list can cause breakage.

---

