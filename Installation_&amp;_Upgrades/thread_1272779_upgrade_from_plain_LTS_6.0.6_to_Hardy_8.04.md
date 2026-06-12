---
title: "upgrade from plain LTS 6.0.6 to Hardy 8.04"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by twan_van_der_poel on 2009-09-22
Guys, 

I upgraded my server from ubuntu lts plain 6.06 to hardy 8.04, after a reboot it did not  came up. in my ip-based kvm i noticed that in the dist-upgrade/main_pre_req.log file, says;  ( in my mounted (disabled) partition )

ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-backports/Release](http://archive.canonical.com/ubuntu/dists/dapper-backports/Release) Unable to find expected entry  main/debian-installer/binary-i386/Packages in Meta-index file (malformed Release file?)
 dist-upgrade/main_pre_req.log:2009-09-14 21:40:16,068 ERROR doUpdate() failed completely

Does anyone have suggestions ?
Do not hasistate to ask for more specs.

Thanks in advance.
Best regards,


Twan van der Poel

---

### Post by Partyboi2 on 2009-09-23
Open up your sources.list and comment out your dapper backports repo.
```
sudo nano /etc/apt/sources.list
```look for 
```
deb http://archive.ubuntu.com/ubuntu/ dapper-backports restricted main multiverse universe
``` and add a # in front of the line and save the changes
Ctrl+o
Enter
Ctrl+x
then back in the terminal 
```
sudo apt-get update
```then try upgrading again.

If unsure still on what to comment out post the output to
```
cat /etc/apt/sources.list
```

---

