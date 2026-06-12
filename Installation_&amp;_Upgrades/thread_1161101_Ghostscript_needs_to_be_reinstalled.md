---
title: "Ghostscript needs to be reinstalled"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by erixoltan on 2009-05-16
I am trying to upgrade this system to Jaunty but Synaptic doesn't work and I can't proceed with the upgrade.  

I put Xubuntu on my Mom's old laptop for her because Windows was causing problems.  She brought it back to me because she needed me to set up the printer.  I tried to run the Synaptic Package Manager and got the following error:

[INDENT]E: The package ghostscript needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
[/INDENT]

It exits after displaying this error.  I can't use Synaptic or apt-get to do anything.  It immediately exits with the same error message: ghost script needs to be installed etc. etc. 

Any advice would be greatly appreciated.  

Thanks,
Erik

---

### Post by erixoltan on 2009-05-16
Nothing I try seems to help with this problem.

Here's what happens when I try to upgrade.```
ildi@ildi-xubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ghostscript needs to be reinstalled, but I can't find an archive for it.
ildi@ildi-xubuntu:~$ 
```Here's what happens when I try to remove ghostscript.```
ildi@ildi-xubuntu:~$ sudo apt-get remove ghostscript
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ghostscript needs to be reinstalled, but I can't find an archive for it.
ildi@ildi-xubuntu:~$ 
```So I'm really ***_frozen_*** here.

---

### Post by erixoltan on 2009-05-17
This problem was solved on another thread.

[http://ubuntuforums.org/showthread.php?t=1162203](http://ubuntuforums.org/showthread.php?t=1162203)

---

