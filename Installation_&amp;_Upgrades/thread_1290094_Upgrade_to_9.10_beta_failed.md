---
title: "Upgrade to 9.10 beta failed"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by castano on 2009-10-13
I've tried to upgrade to the 9.10 beta release, but obtained the following error:

"""
Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
E:Unable to correct problems, you have held broken packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report.
"""

This happened while "Calculating the changes". I've tried upgrading using `upgrade-manager -d` and `do-release-upgrade -d` with the same outcome.

The apt.log file contains the following error messages:

"""
Investigating apparmor
Package apparmor has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 1 as a solution to apparmor 0
Package apparmor has broken dep on sysvinit
  Considering sysvinit 1 as a solution to apparmor 0
  Or group remove for apparmor
Investigating gdm-guest-session
Package gdm-guest-session has broken dep on apparmor
  Considering apparmor 0 as a solution to gdm-guest-session -1
  Removing gdm-guest-session rather than change apparmor
Investigating libc-bin
Package libc-bin has broken dep on libc6
  Considering libc6 10653 as a solution to libc-bin 10002
"""

I could get rid of the first messages by removing apparmor before the install, but the error with libc-bin persisted. In order to understand the problem I changed the distribution in /etc/apt/sources.list and installed libc-bin manually, but apt-get produced the following error:

"""
The following packages have unmet dependencies:
  libc-bin: Breaks: libc6 (< 2.10) but 2.9-4ubuntu6.1 is to be installed
E: Broken packages
"""

On the other side, aptitude is able to resolve the dependencies correctly and upgrade libc6 to the karmic version.

Installing libc-bin manually and retrying the automatic install did not work, since many other packages also had the same issue, so I downgraded the package.

I've never seen this problem reported by anyone else, so I'm assuming this is something specific about my system, and I'm afraid the final release will still have the same issue. Does anybody have any suggestion other than backing up and reinstalling from scratch?

Thanks!

---

### Post by zvacet on 2009-10-13
```
sudo apt-get -f install
```

---

### Post by castano on 2009-10-13
There are no broken packages or conflicts in my current configuration. `apt-get -f install` does not do anything.

---

### Post by kurisu2 on 2009-10-13
Exactly the same problem. I did a clean install of 9.04, installed all updates then tried to upgrade to 9.10 and got the same error message as OP.

---

### Post by castano on 2009-10-13
If you look at the apt.log, these seem to be different issues. In your case you are able to install libc-bin without any problem, but problems arise when trying to install linux-image-generic instead.

---

### Post by kurisu2 on 2009-10-13
Not entirely sure what I did, I ran 

sudo apt-get update
sudo apt-get upgrade
Restarted then tried to update again, seems to have fixed whatever the problem was.

---

### Post by castano on 2009-10-13
None of those things helped in my case. Attached are the log files.

---

### Post by retiredtechie on 2009-10-14
I had a similar problem until I change the software sources to the main repository.

---

### Post by castano on 2009-10-14
I also thought that could help, but no luck :(

---

### Post by castano on 2009-10-18
Turns out I had some pinned packages that were preventing the automatic upgrade. After fixing that problem ubuntu upgraded without any major issue.

---

### Post by quequotion on 2010-05-01
> **kurisu2 said:**
> Not entirely sure what I did, I ran 

sudo apt-get update
sudo apt-get upgrade
Restarted then tried to update again, seems to have fixed whatever the problem was.

Did you do that before or after the upgrade script changed all your sources to lucid?

---

