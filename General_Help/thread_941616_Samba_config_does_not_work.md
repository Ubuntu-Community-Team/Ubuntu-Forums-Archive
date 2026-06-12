---
title: "Samba config does not work"
date: 2008-10-08
forum: General Help
---

### Post by Technofear on 2008-10-08
Hi

I just installed the Samba config tool on Kubuntu. When I select it from Kmenu-system-samba nothing happens. 

I'm not sure how to see Samba itself is running (there is no process named samba). 

How can I confirm this, and how can I configure Samba

---

### Post by geirha on 2008-10-08
The processes are called smbd and nmbd. Try ```
sudo /etc/init.d/samba restart
``` does it give any errors? Also, look at ~/.xsession-errors. It may contain information as to why that app doesn't start.

---

### Post by Technofear on 2008-10-08
well...the processes are running, but there is no xsession-errors file anywhere on the system.

I looked at the command behind the kmenu item and ran it in a console and it appears that it requires x-server (see below).

I guess I need to look at installing this....

/# system-config-samba
system-config-samba requires a currently running X server.

---

### Post by geirha on 2008-10-08
.xsession-errors, not xsession-errors. The . (dot) makes it a hidden file. Try in a terminal. ```
less ~/.xsession-errors
```

I haven't used kubuntu myself, but I think all ubuntu versions log error messages from x in that file.

---

### Post by Technofear on 2008-10-08
I've got a number of errors in the file - the samba start causes 'could not find gksu' executable...

The first error appears to be...
startkde: kpersonalizer not found! Please install to properly configure your user.
kbuildsycoca running...
*** attempt to put segment in horiz list twice
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x1600059
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x1600059


I guess I need to look into this first...


Thanks for your help

---

