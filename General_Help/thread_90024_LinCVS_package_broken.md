---
title: "LinCVS package broken"
date: 2005-11-14
forum: General Help
---

### Post by matthias_k on 2005-11-14
Hi,

I was using LinCVS on Hoary to manage my CVS repositories and found it was a very good frontend. On Breezy however, the package is broken and I can't install it:
> 
matthias:~$ sudo aptitude install lincvs                                                            Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  lincvs: Depends: libqt3c102-mt (>= 3:3.3.3) which is a virtual package.

I don't know where to report this issue, so I thought I'd ask here first.

Regards,
Matthias

---

### Post by matthias_k on 2005-11-14
By the way, can anyone recommend another good CVS frontend so I don't have to mess with the command line meanwhile?

---

