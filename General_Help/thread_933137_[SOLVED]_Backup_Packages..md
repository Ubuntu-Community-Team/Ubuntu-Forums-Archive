---
title: "[SOLVED] Backup Packages."
date: 2008-09-29
forum: General Help
---

### Post by prabath_fun on 2008-09-29
Hi,
  I came to know that, the packages downloaded by synaptic for installation can be backup from the location "/var/cache/apt/archives" location. But, I am getting any packages from this location.
  Please help me to identify.
I am using
   Ubuntu 8.04 in Wubi.

---

### Post by kpkeerthi on 2008-09-29
Did you ever run ```
sudo apt-get autoclean/clean
``` or have ever cleared cache using synaptic?

---

### Post by forger on 2008-09-29
+1, he probably has :)
apt-get autoclean = clears any downloaded package that is obsolete (cannot be found in servers anymore)
apt-get clean = clears all downloaded packages

Can you post the output of this command:
```
dir -lR /var/cache/apt
```

---

### Post by prabath_fun on 2008-09-30
Output of dir -lR /var/cache/apt is 


/var/cache/apt:
total 6776
drwxr-xr-x 3 root root    4096 2008-04-22 23:42 archives
-rw-r--r-- 1 root root 3489381 2008-09-26 21:20 pkgcache.bin
-rw-r--r-- 1 root root 3443029 2008-09-26 21:15 srcpkgcache.bin

/var/cache/apt/archives:
total 4
-rw-r----- 1 root root    0 2008-09-26 21:20 lock
drwxr-xr-x 2 root root 4096 2008-04-22 23:39 partial

/var/cache/apt/archives/partial:
total 0


Please help me.

---

### Post by prabath_fun on 2008-10-13
I got it from the 
/var/cache/apt/archives

With Thanks,
[COLOR="Blue"]Prabath[/COLOR]

---

