---
title: "unable to install GNOME on kubuntu 9.10"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by purct on 2009-11-07
I have upgraded my kubuntu 9.04 to 9.10 in the last week.  before the upgrade GNOME was also installed as a secondary desktop, however after the upgrade it is missing so I have been trying to install GNOME but had no luck...

it seems that there is a problem with unmet-dependencies. I get the following messages when trying to install gnome: 

root@home-laptop:~# apt-get install gnome
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gnome: Depends: gnome-desktop-environment (= 1:2.22.2~4ubuntu8) but it is not going to be installed
         Depends: gnome-vfs-obexftp but it is not installable
E: Broken packages
root@home-laptop:~# apt-get install gnome-desktop-environment
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gnome-desktop-environment: Depends: fast-user-switch-applet (>= 2.22.0) but it is not installable
                             Recommends: fam but it is not going to be installed
E: Broken packages


I have logged a bug for it but I wonder if anyone new a way around it?  is there another REPO that I could use?

---

### Post by purct on 2009-11-08
I solved the issue by installing GNOME-CORE.

---

### Post by Strongman332 on 2009-12-04
this fix did not work for me

---

### Post by McGrude on 2010-02-23
Try this : 

sudo apt-get install ubuntu-desktop

---

