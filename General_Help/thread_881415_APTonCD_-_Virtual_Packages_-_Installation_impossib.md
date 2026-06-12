---
title: "APTonCD - Virtual Packages - Installation impossible"
date: 2008-08-06
forum: General Help
---

### Post by Marcelo Ramone on 2008-08-06
Hello.
 In Ubuntu 8.04.1 I installed aptoncd and I made a CD with all additional packages downloaded via apt. and allocated in the cache.

 In another PC with Ubuntu 8.04.1 without Internet connection  I attempt to install the packages from the CD created adding it as repository, but apt not let me do it because dependencies are not satisfied , because applications depend on libraries that are **"virtual packages"** and are not on the cd ...
 How to solves this?
The dependencies should be solved because all my packages was downloaded with apt and I never delete the apt cache.

 I can't install VLC, gstreamer,plugins, etc., etc., etc.
 I know meta-packages as ubuntu-restricted-extras generate problems because the true-type microsoft fonts are downloaded under demand for the installer from an external repository, but it is not the case, because I do not have that meta-package installed.
 this happens with many applications ...
 Thanks,
Marcelo.-

---

### Post by Moridin333 on 2008-08-06
sounds like the computer that you downloaded with already had some dependencies that your non internet computer didn't have so apt didn't download them.

---

### Post by Marcelo Ramone on 2008-08-06
Looking Synaptic settings, I see that is enabled by default this option: "erase only packages that are no longer available" ([http://img160.imageshack.us/my.php?image=pantallazols3.png](http://img160.imageshack.us/my.php?image=pantallazols3.png))
 Now I put this option in:
"allocate all downloaded packages into the cache" ([http://img80.imageshack.us/my.php?image=pantallazo2hb7.png](http://img80.imageshack.us/my.php?image=pantallazo2hb7.png))
  In section: "not installed (residual configuration)" I see the package "libtunepimp5" ([http://img80.imageshack.us/my.php?image=pantallazo1de6.png](http://img80.imageshack.us/my.php?image=pantallazo1de6.png))
 When I try to install amarok from the CD created with APTonCD, Fails because libtunepimp5 is not present in the CD. That package is not in the APT cache (in this machine) and for that reason when I create the APTonCD not load this package.
 I think the problem occurs because when delete packages on this PC , some dependencies are deleted and do not remain in the cache as I thought...
 But is strange because at this moment I have all gstreamer plugins installed and the same problem occurs when I try to install gstreamer plugins from the APTonCD on the other Machine.

---

