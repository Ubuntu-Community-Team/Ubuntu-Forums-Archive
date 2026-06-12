---
title: "CRON problem (between manual &amp; auto, timed script)"
date: 2008-09-29
forum: General Help
---

### Post by peterseid on 2008-09-29
Hi,

Could anyone please offer some advice on why or how to troubleshoot the following problem:

When running a script from webmin or gnome-schedule manually, it works, otherwise when letting it run (hourly) the script corrupts data (saving to CF card mounted as user subdirectory).

So without going into too much detail of the script, how is it possible, that a script (any script for that matter) would operate differently when run manually (via webmin or gnome-scheduler interface) compared to running via CRON automatically (as user)?

---

### Post by nsche on 2008-09-29
Usually different behavior like this is because the login scripts are not run by a cron job.  You will need to make sure things like your path and any environment variables you need are set up properly.  This is a common problem with the use of cron.

---

### Post by peterseid on 2008-09-30
This is my script:
(tried on Ubuntu 8.04 & Xubuntu 8.04)

#!/bin/bash

ID="IOCP1_"

DATE=`date +%Y%m%d_%H%M%S`;

cd /home/user/data/ > /dev/null 2>&1

curl [http://192.168.70.100/~/test/_DEFAULT_/stop.txt](http://192.168.70.100/~/test/_DEFAULT_/stop.txt) > /dev/null 2>&1

curl -o $ID$DATE.sie [http://192.168.70.100/~/test/_DEFAULT_/data/get/IOCP20080715RevB.sie](http://192.168.70.100/~/test/_DEFAULT_/data/get/IOCP20080715RevB.sie)

curl [http://192.168.70.100/~/test/_DEFAULT_/end.txt](http://192.168.70.100/~/test/_DEFAULT_/end.txt) > /dev/null 2>&1

curl [http://192.168.70.100/~/test/_DEFAULT_/data/delete.txt](http://192.168.70.100/~/test/_DEFAULT_/data/delete.txt) > /dev/null 2>&1

curl [http://192.168.70.100/eDAQ/Test/InitETC?File=/hd/TestETC/IOCP20080715RevB.etc](http://192.168.70.100/eDAQ/Test/InitETC?File=/hd/TestETC/IOCP20080715RevB.etc) > /dev/null 2>&1

curl [http://192.168.70.100/~/test/_DEFAULT_/start.txt](http://192.168.70.100/~/test/_DEFAULT_/start.txt) > /dev/null 2>&1


It basically tells a networked device (192.168.70.100) to stop, saves (via curl commands) a data file to a CF card mounted in the users directory and restarts the device.

Any comments about the script and why it isnt working would be most welcome :) Thanks.

---

### Post by justleen on 2008-09-30
try using the full path to curl, instead of just 'curl'
```

which curl
```

---

### Post by peterseid on 2008-09-30
The curl that loads with the ubuntu software installer (not sure version) does it make a difference?

---

