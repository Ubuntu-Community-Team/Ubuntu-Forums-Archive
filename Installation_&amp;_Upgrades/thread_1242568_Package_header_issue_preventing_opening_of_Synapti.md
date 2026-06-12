---
title: "Package header issue preventing opening of Synaptic Package manager"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by kingzcid3 on 2009-08-17
Following a forced reboot it appears that I've managed to corrupt some package(s) hence the error below. This error is preventing me from downloading new apps as the Update Manager and Synaptic Package Manager applications no longer seem to be working. Help! Any advice on what to do is very welcome. Thanks. 
 
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by ptn107 on 2009-08-17
try
```
sudo aptitude -f install
```
or
```
sudo dpkg --configure -a
```

---

### Post by Soul-Sing on 2009-08-17
Try:
```
sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

---

### Post by ORBstacle on 2009-11-15
[http://ubuntuforums.org/showthread.php?t=453824](http://ubuntuforums.org/showthread.php?t=453824)

---

### Post by brianthefolksinger on 2010-01-12
I got the same error message, not sure what all was going on, appeared after a couple days with no boot and segmentation error meassages.. then it finally rebooted after I went through maybe 48 hrs of memtest (finally cancelled it), but booted then successfully/mysteriously after forcing a hard-drive test.. but had both the package error icon (with above error message) and new hardware driver icon up on the bar. No new drivers though, but attempt to run package manager got the same error message again.. tried some of the solutions.. no go.. what did work was I openned nautilus as root, (sudo nautilus) and deleted the status file ( /var/lib/dpkg/status in the error) which was somehow corrupted.. couldn't open it with gedit, and renamed the status-old file to status, then used sudo gedit to save it again as status-old so I still had it as a backup if this happened again.

now the error icon is gone and synaptic starts fine (so far) haven't tried rebooting yet.. not sure it will and stuff to do first!

I'd like to add that I know nothing about this stuff, technically, just an educated quess that worked, this time.

hmm, I also redid the repositories list as suggested above, though it didn't seem to fix the problem as this did, maybe it helped.. still, I did do it, so should include it.
I am also running ibex on this machine
peace

---

### Post by mirinamulhaq on 2011-04-14
> **leoquant said:**
> Try:
```
sudo rm /var/lib/apt/lists/* -vf
``````
sudo apt-get update
```
yes it worked beautifully.

---

