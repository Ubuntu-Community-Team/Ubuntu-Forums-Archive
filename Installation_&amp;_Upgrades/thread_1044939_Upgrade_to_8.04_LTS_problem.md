---
title: "Upgrade to 8.04 LTS problem"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by yaplimin on 2009-01-19
Attempting to upgrade from 7.10 to 8.04 using Update Manager. I've updated the current version and Update Manager reports "Your system is up-to-date."  Whenever I click on the Upgrade button for the new distribution release, the dialog for "Downloading upgrade tool" appears then disapppears and then nothing happens.

Anyone seen this before?  Any thoughts on why the upgrade is not continuing?
Thanks.

---

### Post by cariboo on 2009-01-19
In a terminal type:

```
sudo update-manager -d
```

according to man update-manager the -d option:

>  -d, --devel-release Check if upgrading to the latest devel release is possible

Jim

---

### Post by yaplimin on 2009-01-20
On this system, I previously successfully upgraded to 7.10 without any problems. Only seeing this when attempting to upgrade to 8.04 LTS.

I tried the suggestion given but it produced the same unsuccessful results. This is the code that was returned in the terminal window:

```
rayap@Shuttle:~$ sudo update-manager -d
warning: could not initiate dbus
extracting '/tmp/tmpp_jUPP/hardy.tar.gz'
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 915, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 202, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 129, in extractDistUpgrader
    tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
  File "/usr/lib/python2.5/tarfile.py", line 1143, in open
    raise ReadError("file could not be opened successfully")
tarfile.ReadError: file could not be opened successfully
```

Please let me know if you know what is causing the read error.  
Thanks.

---

### Post by yaplimin on 2009-01-23
Managed to do the upgrade via the command line:


Backed up /etc/apt/sources.list

In sources.list, replaced every instance of gutsy with hardy

Did sudo apt-get update

Did sudo apt-get dist-upgrade


This appears to have upgraded my system from gutsy (7.10) to hardy (8.04)

---

