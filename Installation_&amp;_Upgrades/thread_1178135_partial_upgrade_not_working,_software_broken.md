---
title: "partial upgrade not working, software broken"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by trozombo on 2009-06-04
Hi, im a newbie with ubuntu. . Ive recently started to have problems when  my upgrade send me to a partial upgrade and then when doing it the little screen just disappears. tried via terminal too but seems to be a problem with  liblexz600core0 which is a file related with a printer that i recently istalled. no idea how to fix this problem !!!help!!!

this is the output from sudo apt-get install -f

chicca@chicca-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  liblexz600core0
0 upgraded, 0 newly installed, 1 to remove and 37 not upgraded.
1 not fully installed or removed.
After this operation, 9433kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 103386 files and directories currently installed.)
Removing liblexz600core0 ...
invoke-rc.d: unknown initscript, /etc/init.d/cupsys not found.
dpkg: error processing liblexz600core0 (--remove):
 subprocess post-removal script returned error exit status 100
Errors were encountered while processing:
 liblexz600core0
E: Sub-process /usr/bin/dpkg returned an error code (1)
chicca@chicca-laptop:~$ 

Thanks!!!!

---

### Post by zvacet on 2009-06-05
```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo dpkg --configure -a
```

```
sudo apt-get --purge remove liblexz600core0
```

---

### Post by trozombo on 2009-06-15
didnt work this is the output

chicca@chicca-laptop:~$ sudo apt-get --purge remove liblexz600core0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  liblexz600core0
0 upgraded, 0 newly installed, 1 to remove and 57 not upgraded.
1 not fully installed or removed.
After this operation, 9433kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 103386 files and directories currently installed.)
Removing liblexz600core0 ...
invoke-rc.d: unknown initscript, /etc/init.d/cupsys not found.
dpkg: error processing liblexz600core0 (--remove):
 subprocess post-removal script returned error exit status 100
Errors were encountered while processing:
 liblexz600core0
E: Sub-process /usr/bin/dpkg returned an error code (1)
chicca@chicca-laptop:~$

---

### Post by wpshooter on 2009-06-15
> **zvacet said:**
> ```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo dpkg --configure -a
```

```
sudo apt-get --purge remove liblexz600core0
```

Zvacet:

I believe there is a minor spelling error in your sage saying.

I think you meant: There is no greater religion, THAN a truth.

---

### Post by trozombo on 2009-07-15
This sound like there s no way out to the problem???
fresh install just like in windows???
mmmmmmm pretty bad
disapointed

---

### Post by condeh on 2009-09-09
I managed to get this installed, which should make it possible to remove.

If you look at the error, it cannot find cupsys

```
invoke-rc.d: unknown initscript, /etc/init.d/cupsys not found
```

so, i went to /etc/init.d and made a symlink from cups to cupsys. this then allowed the installation to complete.

```

john@XubLap:~$ cd /etc/init.d
john@XubLap:/etc/init.d$ sudo ln -s cups cupsys
john@XubLap:/etc/init.d$ aptitude -f install

```

HTH
John.

---

