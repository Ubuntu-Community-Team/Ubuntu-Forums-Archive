---
title: "How to automaticall sync flash drive with backup as shutdown script?"
date: 2008-11-15
forum: General Help
---

### Post by josephellengar on 2008-11-15
I want to have my flash drive sync with my backup folder in ~ whenever I shutdown.  I forget to do the backup all the time and the other day I lost (and later found) my flash drive, which would have been a total disaster if I hadn't found it.  Suggestions?  Intrepid, gnome

---

### Post by iponeverything on 2008-11-15
sysvinit tells the system what to do at startup and shutdown.

What to start/stop and and what order.

Doing what you want to do fairly easy, just create your own init script,
name it so that it is called in the right order during shutdown.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch07_:_The_Linux_Boot_Process](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch07_:_The_Linux_Boot_Process)

---

### Post by uncaspi on 2008-11-15
update-rc.d -f foo.sh start 90 0 6

I think this will do the job. The shell script foo.sh is executed at shutdown. To take backup you must first mount the flash drive and then use rsync to take backup. I.e this foo.sh


#!/bin/bash
mount -t ext3 /dev/sda1 /home/user/flashdrive

rsync -a /* /home/user/flashdrive


Adjust the drives and directories to your need.

---

