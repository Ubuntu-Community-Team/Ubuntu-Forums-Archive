---
title: "Need help upgrading from server 6.06 LTS to 8.04 LTS"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by bzerangue on 2009-10-23
I keep following the [Ubuntu instructions]("https://help.ubuntu.com/community/HardyUpgrades#Network%20Upgrade%20from%206.06%20for%20Ubuntu%20Servers%20(Recommended)") on updating from 6.06 LTS to 8.04 LTS and it keeps telling me that update-manager-core doesn't exist.

```
sudo aptitude install update-manager-core
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "update-manager-core"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
``` 

Here's my sources.list file...

```
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
```

HELP! I need to upgrade to 8.04 LTS as soon as possible. Can anyone help me???

---

