---
title: "finding and killing a ghost package"
date: 2012-01-04
forum: Hardware
---

### Post by happyisland on 2012-01-04
A friend of mine just called me in to try to sort out a problem she encountered while trying to install Canon printer drivers as described in this forum:

[http://ubuntuforums.org/showthread.php?t=1582497](http://ubuntuforums.org/showthread.php?t=1582497)

When I try to follow the instructions I get the following error message from the software center:

dpkg: error processing /home/susanne/Desktop/cnijfilter-mp280series-3.40-1-deb/packages/cnijfilter-common_3.40-1_amd64.deb (--install):

 cnijfilter-common: 3.40-1 (Multi-Arch: no) is not co-installable with cnijfilter-common:i386 3.00-1 (Multi-Arch: no) which is currently installed


I read this to mean that she somehow already installed the 386 version. Problem is, none of those are listed in Synaptic and I can't figure out anyway to uninstall the 386 version. Even worse, I'm not even sure if that's what I need to be doing.

Anybody out there know what the heck is going on over here?

---

### Post by crazy bird on 2012-01-05
I would suggest you to do this: remove all Canon drivers using synaptic. Then check here on how to install a PPA which add a repository for Canon drivers: [https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers](https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers). At the bottom there's a section on how to add the PPA and install the correct Canon driver.

---

