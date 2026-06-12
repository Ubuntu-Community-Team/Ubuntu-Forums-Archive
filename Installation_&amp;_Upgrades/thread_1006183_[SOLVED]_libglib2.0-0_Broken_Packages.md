---
title: "[SOLVED] libglib2.0-0 Broken Packages"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by jdorenbush on 2008-12-09
I am having problems installing themes, gimp, etc. because of some broken packages. Below is the following errors I have received.

```
The following packages have unmet dependencies: libgtk2.0-dev:
Depends: libglib2.0-dev (>= 2.17.6) but it is not going to be installed
Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
Depends: libatk1.0-dev (>= 1.13.0) but it is not going to be installed
E: Broken packages
```


```
The following packages have unmet dependencies: libglib2.0-dev:
Depends: libglib2.0-0 (= 2.18.2-0ubuntu1) but 2.18.2-0ubuntu2 is to be installed
E: Broken packages
```

I tried "[HOWTO fix problems regarding broken dependencies]("http://ubuntuforums.org/showthread.php?t=186672")" but that didn't seem to fix it.

Any help is greatly appreciated, seeing as I am stuck being unable to install a bunch of stuff right now. :(

---

### Post by jdorenbush on 2008-12-10
Anyone? This is problem is rather annoying. I'm stuck, unable to install software. :(

---

### Post by MasterPoulos89 on 2008-12-10
All I know is when I had a broken package I opened the package manager and found a selection that let me see what package was broken and it fixed it. If it doesn't fix it automatically u can uninstall the broken package. Dont know if it will be the same problem for u. It helped me though.

---

### Post by mc4man on 2008-12-10
Certainly try the fix broken in synaptic.

Part of what your problem is, one if not more of the affected packages has been updated to the 'intrepid-update' version but your not getting the updated -dev(s) thru your package manager.

For instance you now have libglib2.0-0 (2.18.2-0ubuntu2) but at best only libglib2.0-0-dev (2.18.2-0ubuntu1) is available to you, hence the error.

There may be other packages with same issue.
(I've noticed some odd goings on with the update manager and synaptic the last few days.

I wouldn't doubt if you searched libglib2.0-0-dev in synaptic it would show no results.

First try running and see if you can update your packages (intrepid-updates
```
sudo apt-get update && sudo apt-get upgrade 
```
Or 
```
sudo apt-get update -o Acquire::http::No-Cache=True
```

Otherwise start here and you should be able to satisfy your deps. by working thru the affected packages. (may take only one or maybe some of the others listed, you'll get the idea. (note you want to use the intrepid-updates versions

[http://packages.ubuntu.com/intrepid-updates/libglib2.0-dev](http://packages.ubuntu.com/intrepid-updates/libglib2.0-dev)

Edit:
It may be that you'll only need the updated libglib2.0-0-dev first, then libpango1.0-dev and  libatk1.0-dev should become installable and you *could* be ok.

---

### Post by jdorenbush on 2008-12-10
The terminal commands didn't do anything.

The deb package installed, but it first prompted me saying something along the lines of, *there are older versions available in the software channel and I should install instead because they are better supported* - I ignored this message. 

Manually installing via [http://packages.ubuntu.com/intrepid/](http://packages.ubuntu.com/intrepid/) worked though. Thanks.

How do I update my Synaptic so it is displaying the latest packages?

---

### Post by mc4man on 2008-12-10
> How do I update my Synaptic so it is displaying the latest packages

I'd just wait it out, things seem to be working better here.

For instance the other day I showed 26 updates including a  kernel update (2.6.27.4 -> 2.6.27.9) and all were greyed out.
Many were available in synaptic and while it was a bit of a chore to manually update the kernel and restricted modules eventually the update manager was able to install the remaining few (6)

Since then things seemed to have 'cleared up' so to speak. (all yesterday I needed to run sudo apt-get update before attempting to install anything new, today things seem back to normal

---

### Post by shadowlands on 2008-12-13
I am having a similar problem.  

E: Type '--19:26:47--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

How do I correct this?  

Help please?

---

### Post by jdorenbush on 2008-12-15
Can you post the contents of that file, */etc/apt/sources.list.d/medibuntu.list*?

1. Run Application (Alt+F2)
2. Type: gedit /etc/apt/sources.list.d/medibuntu.list
3. Copy and paste contents for us to see

---

