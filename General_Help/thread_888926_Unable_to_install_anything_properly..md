---
title: "Unable to install anything properly."
date: 2008-08-13
forum: General Help
---

### Post by Hillside32 on 2008-08-13
Well, I have successfully installed Ubuntu. Unfortunately, when I try to install anything, it gets this error and I'm unable to install it.

Error: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

After that, when I try it, it says this:

dpkg: requested operation requires superuser privilege

I'm an administrator on the computer, do you have to be on the first account? I'll try that now...

---

### Post by Elfy on 2008-08-13
#Yes - to first account, also need to add sudo

```
sudo dpkg --configure -a
```

you gain root right for a short while.

Use gksudo for GUI apps, use sudo for command line.

---

### Post by Hillside32 on 2008-08-13
Wow, thanks. I'll go check if it'll work for the other programs.

---

### Post by waleedakleh on 2009-02-19
> **forestpixie said:**
> #Yes - to first account, also need to add sudo

```
sudo dpkg --configure -a
```

you gain root right for a short while.

Use gksudo for GUI apps, use sudo for command line.
need help when i tried what you suggested this came up
dpkg: status database area is locked by another process

---

### Post by snova on 2009-02-19
> **waleedakleh said:**
> need help when i tried what you suggested this came up
dpkg: status database area is locked by another process

Ensure that you are running no package management programs (Synaptic, apt-get, dpkg, etc.). Then remove the lock file:

```
sudo rm /var/lib/dpkg/lock
```

---

