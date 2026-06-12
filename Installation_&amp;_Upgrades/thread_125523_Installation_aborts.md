---
title: "Installation aborts"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by pkaplan on 2006-02-04
I'm installing kubuntu 5.1.  About 1/3 of the way thru the base install I get the following error:
"The debootstrap program exited with an error (ref value 1).
Check /target/var/log/bootstrap.log for details."
No such file is created to check /target/var/log/ remains an empty directory).

The CD md5summed OK.
Any ideas what's happening/how to fix?

---

### Post by pkaplan on 2006-02-04
More info:
I found a bunch of info from the installer on console 4.
The last 3 lines before I got the above error message are:
base installer: info: Execution hook before debootstrap
base installer: info: Running /var/lib/base-installer.d/01save-logs
base installer: info: Running /var/lib/base-installer.d/40netcfg

Does this help to answer my question?  Why can't I finish installing?
Paul

---

