---
title: "Upgrading from 9.10 beta"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by GARoss on 2009-11-12
I keep getting these "Partial Upgrade" notices from the update manager which might be a no-no, so, I've passed on those. But, I want to fully upgrade to 9.10 from 9.10 beta so is "sudo apt-get upgrade" in the terminal correct?

---

### Post by QIII on 2009-11-12
Do

```
sudo apt-get update
```

and 

```
sudo apt-get upgrade
```

as usual.

You may still get the "partial upgrade" issue.  If you do, don't upgrade.

Then do 

```
sudo apt-get dist-upgrade
```

When that is done (you may have to reboot), do the update/upgrade again to be sure that you are clean and up-to-date.

---

### Post by GARoss on 2009-11-12
Thanks QIII

---

### Post by GARoss on 2009-11-12
> **QIII said:**
>  

```
sudo apt-get dist-upgrade
```

When that is done (you may have to reboot), do the update/upgrade again to be sure that you are clean and up-to-date.

OK. So far, so good. When doing ```
sudo apt-get dist-upgrade
``` it wants to remove *gstreamer0.10-schroedinger & rtkit*. My gut feeling is not to allow that but thought I'd ask. 
Big deal or no?

---

### Post by QIII on 2009-11-12
Unfortunately, I can't make a recommendation because it is not my place to tell you to take a chance on borking your system.

But here is some interesting talk about rtkit

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406702)

gstreamer0.10-schroedinger may be another matter altogether.  Did you install gstreamer through Synaptic?  If you did, you may be able to remove it the same way...

---

