---
title: "upgrading from 8.10 to 9.04"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by tamobe on 2009-08-11
I'm currently running Ubuntu 8.10 and would like to upgrade to 9.04 but the update manager has never given me the option of upgrading.  I just tried switching the Software Source but still the Update Manager simply says "system up-to-date".  Any suggestions?

---

### Post by ubudog on 2009-08-11
Open a terminal (Applications>Accessories>Terminal) and type ```
update-manager -c
```  After that it should say something at the top of the window.  Hope that helps! :P

---

### Post by slakkie on 2009-08-11
If you're not terminal shy, use the following commands

```

# Update your system to the latest and greatest packages
sudo aptitude update && sudo aptitude -s safe-upgrade
# If you are happy with the changes
sudo aptitude -y safe-upgrade
# Start the upgrade process
sudo aptitude install update-manager-core
sudo do-release-upgrade

```

---

### Post by tamobe on 2009-08-19
thanks so much for your help! that worked.

my other question is at the end of the install/upgrade the terminal asked the following:

Setting up gdm (2.20.10-0ubuntu2) ...
Installing new version of config file /etc/gdm/Init/Default ...

Configuration file `/etc/gdm/gdm.conf'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** gdm.conf (Y/I/N/O/D/Z) [default=N] ? z
Type `exit' when you're done.

what does this mean?

---

### Post by Thedosius on 2009-08-20
I'm having the same problem, only the commands entered into terminal did not work. Anything else for me to try?

---

### Post by tamobe on 2009-08-21
hey Thedosius,

In the terminal did you try entering this code (you can just copy and paste it):
sudo aptitude update && sudo aptitude -s safe-upgrade

and then when that's done try the next one (again you can just copy and paste):
sudo aptitude -y safe-upgrade

and then when that's done this one finally (again you can just copy and paste):
sudo aptitude install update-manager-core
sudo do-release-upgrade

---

