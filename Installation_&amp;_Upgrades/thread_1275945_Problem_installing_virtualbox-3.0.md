---
title: "Problem installing virtualbox-3.0"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by partyk1d24 on 2009-09-26
When I try to install virtualbox-3.0 I get the following, but OSE installs fine. Please let me know what I can do....

~$ sudo apt-get -f install virtualbox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-3.0: Depends: libqt4-network (>= 4.4.3) but it is not installable
                  Depends: libqtcore4 (>= 4.4.3) but it is not installable
                  Depends: libqtgui4 (>= 4.4.3) but it is not installable
E: Broken packages

---

### Post by louieb on 2009-09-26
Did you follow the instructions on the [VirtualBox]("http://www.virtualbox.org/") site?   Which version of Ubuntu? Is it up to date?  In the last month have install VirtualBox in both Hardy and Jaunty using those instructions - went without a hitch.   

Check your software sources make sure both universe and multiverse are checked.

---

