---
title: "can not update or install packages"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by roc6977 on 2009-07-21
These are the messages I get:  There is another synaptic running in  non-interactive mode. Please wait for it to finish first.                     and:E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.                   Any ideas, please? thanks, Roc in America

---

### Post by ajgreeny on 2009-07-21
Make sure that Update Manager is not running; it starts all by itself in jaunty, unless you change that configuration.  If it is not, have a look in System Monitor Processes tab for anything to do with synaptic or apt-get, or update, as only one front end for apt-get (or dpkg can be running at any time.  Once you think that nothing else is running that shouldn't be, try the ```
sudo dpkg --configure -a
``` again.

---

### Post by rahjr on 2009-07-21
I have this problem also but I am running 8.04. I have tried sudo dpkg--configure-a but all I get is it cannot be found, this happens with anything I type in the terminal. Thanks for any help.

---

### Post by merlinus on 2009-07-21
sudo dpkg--configure-a

should be

sudo dpkg --configure -a

notice the space between dpkg and -- and configure and -a

---

