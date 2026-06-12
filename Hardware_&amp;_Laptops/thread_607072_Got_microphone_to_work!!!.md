---
title: "Got microphone to work!!!"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by icelechi on 2007-11-08
Hi,
I am not sure whether this will work on all PCs but it worked for my HP dv2617us. 
Anyhoo, it is quite simple

Open a terminal (Applications / Accessories / Terminal) and type in :

sudo cp /etc/esound/esd.conf /etc/esound/esd.conf_backup
gksudo gedit /etc/esound/esd.conf 

Replace all of the text with:

[esd]
# autospawning is not recommended, since it can't really be done
# right.  If you want your login session to be using a sound daemon,
# you should start it from the session controller, not some random
# app inside.
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

Save and close the file. Then go back to the terminal and type in:

sudo /etc/init.d/alsa-utils restart

Restart the computer and Joe's your mum. Mike's working. If it is not working, go back to the terminal and type in the following:

sudo cp /etc/esound/esd.conf_backup /etc/esound/esd.conf

And try to find another way around the problem
HOPE THIS HELPS!!! GOOD LUCK!!

---

