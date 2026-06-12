---
title: "Gutsy Update Error"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by hookzilla on 2009-03-15
When I check for updates, I get this error 

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas how I might correct this?  Any help will be appreciated.  Thanks

---

### Post by taurus on 2009-03-15
If you are running gutsy, how come you have feisty in there?  You should consider removing those repos that have feisty in them in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
Once you've removed feisty, save the file and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by hookzilla on 2009-03-29
Thanks,  Issue solved

---

