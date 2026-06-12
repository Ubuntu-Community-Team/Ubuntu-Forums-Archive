---
title: "Failing to install packages..."
date: 2008-08-27
forum: General Help
---

### Post by johnnykohl on 2008-08-27
Hi,
I am getting the following error when I try to install any driver or update software:

Preconfiguring packages...
dpkg: unable to create '/var/lib/dpkg/updates/tmp.i': No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:

Been stumped on this a couple days and can't seem to find a workaround.
Any help would be greatly appreciated!
Thanks :)
-John

---

### Post by iaculallad on 2008-08-27
For a workaround, try this on your terminal:

```
sudo touch /var/lib/dpkg/updates/tmp.i
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by johnnykohl on 2008-08-27
Yeah I still can't get it
I'm not sure exactly what happened to tmp.i...


/$ sudo touch /var/lib/dpkg/updates/tmp.i 
touch: cannot touch `/var/lib/dpkg/updates/tmp.i': No such file or directory

/$ sudo ls -la /var/lib/dpkg/updates/
ls: cannot access /var/lib/dpkg/updates/tmp.i: No such file or directory
total 8
drwxr-xr-x 2 root root 4096 2008-08-24 15:12 .
drwxr-xr-x 7 root root 4096 2008-07-31 17:20 ..
-????????? ? ?    ?       ?                ? tmp.i

---

### Post by mssever on 2008-08-27
> **johnnykohl said:**
> -????????? ? ?    ?       ?                ? tmp.i
Looks like disk corruption to me. Try running fsck.

---

