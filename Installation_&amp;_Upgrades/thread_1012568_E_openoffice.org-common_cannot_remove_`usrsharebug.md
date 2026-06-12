---
title: "E: openoffice.org-common: cannot remove `/usr/share/bug/openoffice.org-common/presubj"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by nulesus on 2008-12-16
Ubuntu 8.04 (hardy)
Kernel Linux 2.6.24-21-eeepc
GNOME 2.22.3
hardware: Asus eeepc 1000 with SSD

OpenOffice  version 1:2.4.1-1ubuntu2  failed to upgrade so I tried removing it via Synaptic.
It errors with...
```

E: openoffice.org-common: cannot remove `/usr/share/bug/openoffice.org-common/presubj'

```
Not sure if this is corupted by Openoffice or maybe Reiserfs
Note: root and home is formatted Reiserfs on a SSD

I tried to remove manually...
```

root@nulesus:/usr/share/bug/openoffice.org-common# ls -galh
ls: cannot access presubj: Permission denied
total 2.5K
drwxr-xr-x  2 root   72 2008-09-05 12:46 .
drwxr-xr-x 74 root 2.7K 2008-12-15 23:10 ..
??????????  ? ?       ?                ? presubj
root@nulesus:/usr/share/bug/openoffice.org-common# rm -rf presubj 
rm: cannot remove `presubj': Permission denied
root@nulesus:/usr/share/bug/openoffice.org-common# 

```
I even tried chmod -R 777

How do i get rid of this file? Even as root I can't remove it.

---

### Post by inobe on 2008-12-16
hi and welcome


what is the tutorial you used to upgrade ?

here is one that may help

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

here's the thing' you could remove some core components attempting removal of a previous version.

---

### Post by nulesus on 2008-12-16
Thanks  inobe that looks like a great tutorial.
But I never mention OpenOffice v3

I was just doing a minor update.

---

### Post by nulesus on 2008-12-16
I tried the suggestions in this post...
[http://ubuntuforums.org/showthread.php?t=456714](http://ubuntuforums.org/showthread.php?t=456714)

However, I keep getting Permission denied for everything

```

chmod: cannot access `presubj': Permission denied
root@nulesus:/usr/share/bug/openoffice.org-common# ls -il presubj 
ls: cannot access presubj: Permission denied

```

---

### Post by inobe on 2008-12-16
i am uncertain why you are experiencing that privilege error,, i do get hundreds of hits searching google.

[http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=Adn&q=openoffice.org+presubj&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=Adn&q=openoffice.org+presubj&btnG=Search)

i hope you resolve this and post back with the solution :)

---

