---
title: "synaptic did not finish, how to fix?"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-07-09
I need to install testdisk.

I went to System>Administration>Synaptic package manager and selected testdisk, "mark for installation", "install", etc.

Just as it was about to finish a message box opened up and said something about a failure and to manually run "sudo dpkg --configure -a" which I did.

And these are the results:

> $ sudo dpkg --configure -a
Setting up libc6 (2.9-4ubuntu6) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: Writing of cache data failed: No such file or directory
dpkg: subprocess post-installation script returned error exit status 1

and now I'm stuck.  Synaptic won't run.  When I try it I get a message box:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


If I try to "purge", this is the result:

> $ sudo aptitude purge testdisk
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 


Any and all suggestions would be greatly appreciated.

---

### Post by Sef on 2009-07-09
```
sudo dpkg --configure -a
```Have you run that command from the terminal?  Applications > Accessories > Terminal then copy and paste the command in.

If that works, then try synaptic again.

---

### Post by raymondvillain on 2009-07-09
Yes, I did just that and the results are in the first quote box.

Update:
I deleted a file:

sudo rm /var/lib/dpkg/003 (or something like that), then sudo apt-get update

and things are better.  At least I can get synaptic working again.

But what did I do wrong, in the first place?  Or what went wrong?

---

