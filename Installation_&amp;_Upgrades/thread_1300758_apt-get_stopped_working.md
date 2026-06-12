---
title: "apt-get stopped working"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by ndefontenay on 2009-10-25
Hello,

I tried opening Add/Remove from the Applications Menu, it would show a window in the blink of an eye and close it right away. 


I also got the error: 
a Problem occured while checking for updates in my system tray.

Finally, I tried to do a manual update and basically I can type anything literally and I always get the same error:

sandra@bliss:~$ sudo apt-get install -f
Segmentation faultsts... 0%
sandra@bliss:~$ sudo apt-get dist-upgrade
Segmentation faultsts... 0%
sandra@bliss:~$ sudo apt-get install conky
Segmentation faultsts... 0%
sandra@bliss:~$ sudo apt-get install test
Segmentation faultsts... 0%

I was thinking about re-installing it but then I realized that I don't know how to actually install the installer! It's kind of the chicken and the egg. Which comes first.

---

### Post by myle on 2009-10-25
Does aptitude work?

---

### Post by ndefontenay on 2009-10-25
Darn. Aptitude says this:

sandra@bliss:~$ aptitude
Ouch!  Got SIGSEGV, dying..

This doesn't bode well :(

---

### Post by ndefontenay on 2009-10-25
```
cd /var/cache/apt
rm pkgcache.bin srcpkgcache.bina
```

This fixed it. No idea what happened.

---

### Post by zeero_k on 2010-09-29
I was having the same problem running aptitude on my server; deleting these two files solved the problem. (Note: there is a typo in one of the filenames in the above post, see below for the corrected code)

> **ndefontenay said:**
> ```
cd /var/cache/apt
rm pkgcache.bin srcpkgcache.bin
```

This fixed it. No idea what happened.

---

