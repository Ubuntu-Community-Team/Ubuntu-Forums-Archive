---
title: "Flash Broken after upgrade from backport."
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by cantormath on 2009-05-19
Im on ubuntu hardy 8.04 amd64
I made the mistake of adding the backports below to my sources list.

```
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
  deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
  deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
```I did an apt-get update/upgrade, and now my flash is broken.  It seems to have upgraded to Flash 10 (flashplugin-nonfree).  I tried uninstalling it and installing the old version of flash (ver 9) and I get nothing. Regardless of what version of flash is installed, neither Hulu, nor Youtube sees that I have flash installed.  Flash worked perfectly before upgrading.

Any help is welcome.

---

### Post by cantormath on 2009-05-19
Nevermind......! Got it :-)

So this is what I did.

I commented out the repos in my orginal post, then in terminal
```

:~$ sudo apt-get clean
:~$ sudo apt-get autioclean
:~$ sudo apt-get update
:~$ sudo apt-get remove --purge flashplugin-nonfree
:~$ sudo apt-get install flashplugin-nonfree
```restarted the browser, and youtube worked.  Im now using the older version of flash (ver-9).  DUH..

---

