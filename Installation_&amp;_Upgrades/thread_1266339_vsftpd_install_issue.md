---
title: "vsftpd install issue"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by gnw2 on 2009-09-14
I have an intel system wit Gutsy 7.10 installed.
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"


When I try to apt-get install vsftpd  I get the following error:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main vsftpd 2.0.5-2ubuntu2
  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/vsftpd/vsftpd_2.0.5-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/vsftpd/vsftpd_2.0.5-2ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.140 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


When I look at: ttp://us.archive.ubuntu.com/ubuntu/pool/main/v/vsftpd, 2.05-x is missing.

What do I do to get vsftpd installed?

---

### Post by Partyboi2 on 2009-09-15
Gutsy has reached its end of life, so I would suggest upgrading to a later version of Ubuntu as it keeps your system current with updates.
If you need to use Gutsy and do not want to upgrade then you will need to edit your /etc/apt/sources.list and # out all the lines starting with deb and add the following to the bottom of the file
```
gksu gedit /etc/apt/sources.list
```
```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```
Then save the changes and close gedit and back in the terminal
```
sudo apt-get update && sudo apt-get install vsftpd
```

---

### Post by gnw2 on 2009-09-15
Thanx.  I guess I need to go to 8.04 and then 8.10.
 
Recently lost my sysadmin, so I will do some studying first.
 
Thanx again.

---

### Post by Partyboi2 on 2009-09-16
> Thanx.  I guess I need to go to 8.04 and then 8.10.
Yes that is correct, you cannot jump releases, the only exception to that is if you are upgrading from a LTS (Long term Support) release to another LTS.

---

