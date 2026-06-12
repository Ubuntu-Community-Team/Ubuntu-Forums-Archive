---
title: "Problems after DISTRUBUTION UPGRADE ????"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by ak331 on 2009-11-04
Problems after I upgrade from 9.04 to 9.10

Every time I run upgrade manager i have this strange message and I have looked for the answers in the forum.


when I start update manager it starts with the following message:

> Not all updates can be installed.
run a partial upgrade, to install as many update as possible.
this can be caused by:
* a previous upgrade which did not complete.
* Problem with some of the installed software.
* unofficial software packages not provided by ubuntu.
* Normal changes of a pre-release version of ubuntu.
 
    upgrade                 stop


when I hit upgrade it goes through the process of what was first message while upgrading to 9.10/

> 
preparing for the upgrade.
downloading pacakges
installing packages
cleaning up
start the computer.


then following message pops up 

> Error authenticating some packages
It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

this is followed by another window which says that 

>  See below for a list of unauthenticated packages.

gcc-4.2-base



[http://ubuntuforums.org/images/smilies/icon_mad.gif](http://ubuntuforums.org/images/smilies/icon_mad.gif)

---

### Post by grandtoubab on 2009-11-04
partial upgrade is not safe
[http://ubuntuforums.org/showthread.php?t=1286309](http://ubuntuforums.org/showthread.php?t=1286309)

Ensure you have only Karmic as references in your software list.
Systeme -> Administration -> software sources
Uncheck all references to other address than ubuntu karmic
in a terminal 
to manage your software list:
```

sudo apt-get update
```to upgrade your packages:
```

sudo apt-get upgrade
```to ensure you have all the new packages:

```
sudo apt-get dist-upgrade
```

---

### Post by ak331 on 2009-11-04
Thanks.

It helped a lot and no more partial upgrade error.

---

