---
title: "Please Help me Remove Ubuntu Tweak!"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by LukonLinux on 2009-10-16
I inadvertently installed Ubuntu Tweak, and now I can't get rid of it!

I have opened it (looking for an unistall,) but never used it, so I don't think it has changed anything.  I have tried Synaptic to remove it (no joy,) and I have tried removing it from terminal (same errors.)

I searched the forums, and found this guys post (below.) He was able to solve his display problem, but never got rid of Ubuntu Tweak.  Every time I run Update Manager, I get errors related to Ubuntu Tweak, and I want it off my system.  Any help would be greatly appreciated.


  **Accidentally installed wrong version of ubuntu tweak, Now I can't remove it.**             
                                                                Hi. I need help: 

I accidentally installed the version of ubuntu tweak for Karmic on my Jaunty distro, and it has messed up my menu's. Not that bad, just made them semi-transparent, but still annoying. So i wanted to remove it again, by typing;

$ sudo apt-get remove --purge ubuntu-tweak

And I get an error: 
 
Do you want to continue [Y/n]? y
(Reading database ... 232262 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--purge):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas how to get rid of this foul presence? Thanks in advance. 

Cheers.

---

### Post by Kevbert on 2009-10-16
Please take a look at [[COLOR="Red"]this[/COLOR]]("http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/").

---

