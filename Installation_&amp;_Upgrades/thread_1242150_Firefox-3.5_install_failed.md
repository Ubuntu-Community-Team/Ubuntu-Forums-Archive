---
title: "Firefox-3.5 install failed"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by Waappu on 2009-08-16
Hi

I did try install firefox-3.5, but my pc crash during install.

Firefox-3.5 is not working and if I try uninstall I just get errors
```
sudo apt-get remove firefox-3.5 --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox-3.5*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 3609kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 126955 files and directories currently installed.)
Removing firefox-3.5 ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing firefox-3.5 (--purge):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox-3.5
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas how I can fix this problem ?

Thanks advance

---

### Post by Waappu on 2009-08-16
Hi

I fixed problem
```
sudo rm /var/lib/dpkg/info/firefox-3.5*
sudo dpkg --remove --force-depends --force-remove-reinstreq firefox-3.5 firefox-3.5-branding
```
and then re-installed again.

---

