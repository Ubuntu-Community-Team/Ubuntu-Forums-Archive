---
title: "Problem installing Eclipse"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by dvlchd3 on 2009-02-10
Recently I experienced a problem while attempting to install several packages.  I was installing Eclipse with C++ support, however, after leaving my laptop for a while, the screensaver came on.  After returning to my laptop, Ubuntu would not come back from the screensaver.  Without thinking, I forced the computer off.  (I had forgot I was actually doing something important.  I should have just waited...I know).

Now it seems I can't install anything.  Eclipse is not working properly, and neither is g++.  They showed as they are installed in Synaptics.  At first anytime I attempted to install new packages, I got a long list of packages that could not be setup properly.  After running apt-get -f install and dpkg --configure -a without any success, I ran the command dpkg --remove-selections.  This seemed to fix the problem.

However, recently there was a few updates.  I attempted installing the updates, however, I get the following error messages:

```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libecj-java-gcj
The following packages will be upgraded:
  brasero firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support libbrasero-media0 libc6 libc6-dev libc6-i686 libsqlite3-0 sqlite3 xulrunner-1.9 xulrunner-1.9-gnome-support
14 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B/20.9MB of archives.
After this operation, 4469kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 198966 files and directories currently installed.)
Removing libecj-java-gcj ...
gcj-dbtool-4.3: symbol lookup error: /usr/lib/libgcj.so.90: undefined symbol: _ZN3org3omg5CORBA8p/rtable16BoxedValueHelper6class$E
dpkg: error processing libecj-java-gcj (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 libecj-java-gcj
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've never ran into a problem with apt-get before.  On occasion Synaptics fails on me, and few commands fix the problem, however, I've stretched my brain on this one.

In summary:  All packages and dependencies for Eclipse with C++ support (I'm not sure of all the packages) are not installed correctly.  I can't install most packages now.  (I'm assuming this is because of the dependencies that Ubuntu thinks are installed and configured properly, but aren't).  I've also attempted reinstalling all the Eclipse, GCC, and G++ packages, however, Synaptics locks up on me.

I'm not sure what logs to view for this, but I'd appreciate any help someone can give me.

---

