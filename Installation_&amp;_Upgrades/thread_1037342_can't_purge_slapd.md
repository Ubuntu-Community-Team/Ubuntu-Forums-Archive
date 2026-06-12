---
title: "can't purge slapd"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by bandito40 on 2009-01-11
Hi,

I have been trying to remove slapd with apt-get, aptitude and  synaptic but I keep getting the following error:

```

Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdb4.2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  slapd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 3965kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 120903 files and directories currently installed.)
Removing slapd ...
/etc/default/slapd: line 2: suffix: command not found
invoke-rc.d: initscript slapd, action "stop" failed.
dpkg: error processing slapd (--purge):
 subprocess pre-removal script returned error exit status 127
/etc/default/slapd: line 2: suffix: command not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I get the same error when I try using **apt-get -f install** to correct the error.

Anyone have any ideas how I could fix this?

Thanks,


Bandito

---

### Post by Partyboi2 on 2009-01-11
Try removing the /etc/default/slapd file out of the way.
```
sudo mv /etc/default/slapd /etc/default/slapd.old
```
```
sudo apt-get remove --purge slapd
```

---

### Post by bandito40 on 2009-01-11
That seamed to do the trick.  Just out of curiosity, what exactly happened when the two specified commands are given.

Thanks,


Bandito

---

### Post by albinootje on 2009-01-11
> **bandito40 said:**
> That seamed to do the trick.  Just out of curiosity, what exactly happened when the two specified commands are given.

The first command moves (renames) that file.

The second command tells apt-get to remove the slapd package *and* remove the system-wide configuration generated from the package slapd.

---

