---
title: "CUPS fails to start/install"
date: 2011-10-18
forum: Hardware
---

### Post by Forum Newbie on 2011-10-18
I updated to Ubuntu 11.10 and since then my printer could not be seen. I'm a bit of a novice so I started reading and saw that CUPS was likely the culprit. I attempted to start the service and failed. I then tried to install by building from the source to no avail. From there I tried to uninstall then reinstall from the Ubuntu Software Center. It said it failed and the details are shown below. I'm not Linux savvy enough to figure out what this means, suffice to say that CUPS service wouldn't start and I'm not certain why. Any assistance would be greatly appreciated. Thanks in advance. 

installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 171352 files and directories currently installed.) 
Removing ubuntu-desktop ... 
Removing foomatic-db-compressed-ppds ... 
Selecting previously deselected package cups. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 171344 files and directories currently installed.) 
Unpacking cups (from .../cups_1.5.0-8ubuntu1_amd64.deb) ... 
Selecting previously deselected package cups-driver-gutenprint. 
Unpacking cups-driver-gutenprint (from .../cups-driver-gutenprint_5.2.7-2ubuntu4_amd64.deb) ... 
Selecting previously deselected package foomatic-db. 
Unpacking foomatic-db (from .../foomatic-db_20110831-0ubuntu3_all.deb) ... 
Processing triggers for ureadahead ... 
Processing triggers for ufw ... 
Processing triggers for doc-base ... 
Processing 1 added doc-base file... 
Registering documents with scrollkeeper... 
Processing triggers for man-db ... 
Setting up cups (1.5.0-8ubuntu1) ... 
start: Job failed to start 
invoke-rc.d: initscript cups, action "start" failed. 
dpkg: error processing cups (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of cups-driver-gutenprint: 
 cups-driver-gutenprint depends on cups (>= 1.3.0); however: 
  Package cups is not configured yet. 
dpkg: error processing cups-driver-gutenprint (--configure): 
 dependency problems - leaving unconfigured 
Setting up foomatic-db (20110831-0ubuntu3) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 cups 
 cups-driver-gutenprint 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
Setting up cups (1.5.0-8ubuntu1) ... 
cups start/running 
Setting up cups-driver-gutenprint (5.2.7-2ubuntu4) ... 
Did not update any PPD files 
reload: Not running 
invoke-rc.d: initscript cups, action "force-reload" failed. 
..... 
lpstat: No such file or directory

---

### Post by retrokid on 2011-10-19
I am having the same issue. I managed to install cups from source but still had problems with the print driver permissions afterwards. I will post here if I figure it out.

---

### Post by retrokid on 2011-10-19
Try opening a terminal window and entering the following:

```
sudo apt-get purge cups && sudo apt-get autoremove
sudo apt-get update && sudo apt-get install cups
```

---

### Post by Forum Newbie on 2011-10-19
> **retrokid said:**
> Try opening a terminal window and entering the following:

```
sudo apt-get purge cups && sudo apt-get autoremove
sudo apt-get update && sudo apt-get install cups
```

That seems like it may have worked. It no longer says the service isn't running. I'll find out after work whether or not I can find the printer, but it's looking good so far, so thank you.

---

### Post by Forum Newbie on 2011-11-17
It worked! Thanks so much for the assist! Sorry for it taking so long to get back to this.

---

