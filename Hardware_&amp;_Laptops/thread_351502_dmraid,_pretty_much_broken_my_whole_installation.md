---
title: "dmraid, pretty much broken my whole installation"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by lukeo on 2007-02-02
DMRAID is driving me nuts.

As you've probably read the version in 6.10 is broken.

apt-get install --reinstall dmraid

fails

apt-get remove dmraid

fails with

```
 * Setting up DMRAID devices...                                                 /etc/init.d/dmraid: line 13: 15987 Segmentation fault      (core dumped) /sbin/dmraid --activate yes --ignorelocking >/dev/null 2>&1
invoke-rc.d: initscript dmraid, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 /var/cache/apt/archives/dmraid_0.9.9+1.0.0.rc9-2ubuntu1_i386.deb

```

now running synaptic gives me an error, running apt-get -f install gives me an error too... basically I cannot install or remove anything anymore every single things I do gives me a 

An error has occured:
/var/cache/apt/archives/dmraid_0.9.9+1.0.0.rc9-2ubuntu1_i386.deb: subprocess new pre-removal script returned error exit status 139

Any thoughts on why I can't remove/delete/update to a working version of dmraid? and why it's now shagged my entire install... really damn annoying and off putting.

---

### Post by lukeo on 2007-02-03
seems no one knows much about dmraid?

[http://www.ubuntuforums.org/showthread.php?t=288094](http://www.ubuntuforums.org/showthread.php?t=288094)

that thread also a distinct lack of anyone responding to a similair issue.

---

### Post by lukeo on 2007-02-03
bump!

even though I've re-installed ubuntu I'd still like a few answers if anyone knows!

---

