---
title: "Update error, and documentation fail"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by odoketa on 2008-12-11
Hi,

When I ran the software updater today, I got an error on load, which said something like 'unable to access e:\cache, please report error'. I would paste the exact text, but the copy paste from the error message didn't work.

I don't have an e: drive, so I'm not sure what that was all about. But I decided to report it (since it asked me to). However, the documentation seems to indicate I should select 'help -> report error' (or something similar) from the menu, but there is no 'help' menu - only Apps, Places, and System. So that was... confusing.

So, in short, if someone could tell me (a) what the fastest way to report errors of this type are, and (b) how I can fix the documentation (once I know what the documentation should say), I would appreciate it. Also, is anyone else having this weird cache error message?

Thanks,
David

---

### Post by taurus on 2008-12-11
Close update-manager if you have it open.  Then, open a terminal and run this command.  Post the output here.

Applications -> Accessories -> Terminal
```
sudo apt-get update
```

---

### Post by cariboo on 2008-12-11
If you think you have found a bug you can go here:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

and report the bug, you will have to create an account to be able to do so. 

I would suggest searching for the error you got before you submit a bug in order not to duplicate the bug report.

Jim

---

### Post by bobnewbie on 2009-06-16
I have an update error and tried your sudo apt-get update and wound up with the same error again:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
Any assistance much appreciated.
Thanks

---

### Post by Therion on 2009-06-16
Open a Terminal and paste in:
```
sudo dpkg --configure -a
```

---

