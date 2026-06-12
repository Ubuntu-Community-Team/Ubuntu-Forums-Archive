---
title: "Can't remove packages"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by maff130 on 2009-07-16
Hey,

I was in the middle of installing lastmp and lastfmsubmitd when my laptop froze. I had to reboot, but now I can't do anything with apt, I just get messages like this:

```
root@maff-laptop:/home/maff# aptitude install lastmp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
The following partially installed packages will be configured:
  lastfmsubmitd lastmp python-musicbrainz 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up lastfmsubmitd (0.37-3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing lastfmsubmitd (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of lastmp:
 lastmp depends on lastfmsubmitd; however:
  Package lastfmsubmitd is not configured yet.
dpkg: error processing lastmp (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up python-musicbrainz (2.1.5-2ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-musicbrainz (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 lastfmsubmitd
 lastmp
 python-musicbrainz
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done

```

I can't uninstall or reinstall any of the affected packages, how do I fix this? :(

Edit: I'm running Crunchbang 9.04, if it helps.

Edit: Alot of faffing about with deleting package stuff manually, apt-get installing and removing, and manually creating config files later, and everything works again. Feel free to close this thread.

---

