---
title: "Cron auto update errors"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Millage on 2009-04-23
I have cron set to the following:
MAILTO=me@myaddress
0 0 * * * apt-get update && up-gate -y upgrade

This morning, my email had errors in it, and a quick check showed that the updates did not install.

```
Get:1 http://security.ubuntu.com intrepid-security Release.gpg [189B]
Hit http://us.archive.ubuntu.com intrepid Release.gpg
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Get:2 http://security.ubuntu.com intrepid-security Release [51.2kB]
Hit http://us.archive.ubuntu.com intrepid Release
Hit http://us.archive.ubuntu.com intrepid-updates Release
Hit http://us.archive.ubuntu.com intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Get:3 http://security.ubuntu.com intrepid-security/main Packages [106kB]
Get:4 http://security.ubuntu.com intrepid-security/restricted Packages [3517B]
Get:5 http://security.ubuntu.com intrepid-security/main Sources [29.6kB]
Get:6 http://security.ubuntu.com intrepid-security/restricted Sources [1154B]
Get:7 http://security.ubuntu.com intrepid-security/universe Packages [48.4kB]
Get:8 http://security.ubuntu.com intrepid-security/universe Sources [8347B]
Get:9 http://security.ubuntu.com intrepid-security/multiverse Packages [6729B]
Get:10 http://security.ubuntu.com intrepid-security/multiverse Sources [1860B]
Fetched 257kB in 2s (86.7kB/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be upgraded:
  firefox firefox-3.0 firefox-3.0-branding xulrunner-1.9
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8705kB of archives.
After this operation, 8192B of additional disk space will be used.
Get:1 http://security.ubuntu.com intrepid-security/main xulrunner-1.9 1.9.0.9+nobinonly-0ubuntu0.8.10.1 [7547kB]
Get:2 http://security.ubuntu.com intrepid-security/main firefox-3.0-branding 3.0.9+nobinonly-0ubuntu0.8.10.1 [202kB]
Get:3 http://security.ubuntu.com intrepid-security/main firefox-3.0 3.0.9+nobinonly-0ubuntu0.8.10.1 [887kB]
Get:4 http://security.ubuntu.com intrepid-security/main firefox 3.0.9+nobinonly-0ubuntu0.8.10.1 [69.0kB]
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin: 
Fetched 8705kB in 14s (588kB/s)
dpkg: `ldconfig' not found on PATH.
dpkg: `start-stop-daemon' not found on PATH.
dpkg: `install-info' not found on PATH.
dpkg: `update-rc.d' not found on PATH.
dpkg: 4 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

How do I fix this?

---

