---
title: "Error while open update manager 8.10"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by tusherr on 2009-02-18
When I am trying to update my Ubuntu 8.10 it shows me a error message. The message is:
 
E:Problem parsing dependency Pre-Depends, E:Error occurred while processing libgl1-mesa-glx (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

What should I do now?

---

### Post by Shazaam on 2009-02-18
Try this...
Open terminal and enter this...
```
gksudo nautilus
```
This will open nautilus as root, be careful. Drill down to /var/lib/dpkg, find the two "status" files (status and status-old) rename status to-
```
status.bak
```
then rename status.old to-
```
status
```
Close nautilus and enter this in terminal...
```
sudo apt-get update && sudo apt-get upgrade
```
If it returns no errors, run these two in terminal...
```
sudo dpkg --configure -a
```
and
```
sudo apt-get install -f
```

---

