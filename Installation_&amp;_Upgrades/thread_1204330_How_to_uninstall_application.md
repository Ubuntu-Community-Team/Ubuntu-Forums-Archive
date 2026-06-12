---
title: "How to uninstall application"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by julio prada on 2009-07-04
I tried to uninstall the "contacts-snapshot" application using Ubuntu add/remove, synaptic, apt, aptitude with no results.

I think the problem started with a bad installation and now I can not reinstall it.

Is there a way to manually remove the files so that I can install it again?

Below is the result of the aptitude command, where I get a "unable to execute pre-removal script" error.

Thanks a lot!!!!

----------------------------------------------------------------
jprada@jprada-laptop:~$ sudo aptitude purge contacts-snapshot
[sudo] password for jprada:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  contacts-snapshot{p} linux-headers-2.6.28-11{u} 
  linux-headers-2.6.28-11-generic{u} 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 75.1MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 144629 files and directories currently installed.)
Removing contacts-snapshot ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing contacts-snapshot (--purge):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 contacts-snapshot
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
----------------------------------------------------------------------

---

### Post by merlinus on 2009-07-04
Did you try

```
sudo apt-get remove --purge contacts-snapshot
```

---

### Post by earthpigg on 2009-07-04
perhaps try reinstalling it, then removing it?

i highly suggest not trying to uninstall by deleting the individual files and directories.

---

