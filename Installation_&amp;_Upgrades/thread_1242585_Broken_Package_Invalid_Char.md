---
title: "Broken Package Invalid Char"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by baderd on 2009-08-17
Hey Folks,

   I ran into some troubles while letting the update manager keep my system in tip top shape. I now have three broken packages all related to the kernel which makes me a little nervous. They are, 

linux-headers-2.6.28-14-generic
linux-image-generic
linux-restricted-modules-2.6.28-14-generic. 

Oh, I should say that I'm running on an AMD system in 64bit mode. 

Anyway, when I try and remove the packages I get an error message that says...

dpkg parse error in file '/var/lib/dpkg/status' near line 38662 package 'blt': 'Depends' field, Invalid package name 'tcl8.$': character '$' not allowed

So obviously the blt pkg wanted to make sure that the version of tcl was at 8.x but apparently that wasn't the proper way to specify. 

So, do I go edit that file and remove that offending Depends element (since i want tcl to stay anyway) so that I can then use the synaptic package manager to remove my broken packages? 

Or will dpkg -P take care of this without the '$' wildcard pooching my entire software archive? 

Much Thanks, -Dan.

---

### Post by Partyboi2 on 2009-08-18
You could remove the  Invalid character or you could try  to replace your current '/var/lib/dpkg/status' with the '/var/lib/dpkg/status-old' file
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.broke
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
Then
```
sudo apt-get -f install
```

---

### Post by baderd on 2009-08-18
> **Partyboi2 said:**
> You could remove the  Invalid character or you could try  to replace your current '/var/lib/dpkg/status' with the '/var/lib/dpkg/status-old' file
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.broke
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
Then
```
sudo apt-get -f install
```

Well, since the two files are exactly the same size (to the byte) I'm guessing there isn't much difference between status.old and status. But, just for the heck of it I'll give it a try. 

Any ideas for what I should change the character to? Find the correct version of tcl on my system and use that? Or will it matter since it's in a "Depends" clause and shouldn't be removed anyway? 

Thanks- Dan.

---

### Post by Partyboi2 on 2009-08-19
Have a look for this part
```
Package: blt
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 3904
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 2.4z-4.1
Replaces: blt-common, blt-demo (<< 2.4i-1), blt-dev (<< 2.4z-3), blt4.2, blt8.0, blt8.0-unoff
Provides: blt-common
**[COLOR=Red]Depends: libc6 (>= 2.4), libx11-6, tcl8.$ (>= 8.5.0) | tcl8.4 (>= 8.4.16), tk8.5 (>= 8.5.0) | tk8.4 (>= 8.4.16)[/COLOR]**
Suggests: blt-demo
Conflicts: blt-common, blt4.2, blt8.0, blt8.0-unoff
Description: the BLT extension library for Tcl/Tk - run-time package
 BLT is a library of useful extensions for the Tcl language and the
 popular Tk graphical toolkit.  It adds a vector and tree data type,
 background execution and some debugging tools to Tcl, and provides
 several new widgets for Tk, including graphs, bar-charts, trees, tabs,
 splines and hyper-links, as well as a new geometry manager, drag &
 drop support, and more.
 .
 This package contains everything you need to use BLT with your Tcl/Tk
 scripts and Tcl/Tk-enabled apps.
 .
 Homepage: http://blt.sourceforge.net/
Original-Maintainer: Chris Waters <xtifr@debian.org>
```

On the red line look for the $ and replace it with either 8.5 or 8.4, have a look what's in the brackets for a clue to which one it is so for example:
tcl8.? (>= 8.5.0) = 8.5
tcl8.? (>= 8.4.16) =8.4

---

### Post by epsolon77 on 2009-08-26
I had a similar issue and edited the status file.  There was a bad character in a description that I was able to identify because of this thread.  Thank you.

---

### Post by baderd on 2009-08-28
Ok, I don't see any offending characters here, do you? 


```
Package: blt
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 4400
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 2.4z-4.1
Replaces: blt-common, blt-demo (<< 2.4i-1), blt-dev (<< 2.4z-3), blt4.2, blt8.0, blt8.0-unoff
Provides: blt-common
Depends: libc6 (>= 2.4), libx11-6, tcl8.5 (>= 8.5.0) | tcl8.4 (>= 8.4.16), tk8.5 (>= 8.5.0) | tk8.4 (>= 8.4.16)
Suggests: blt-demo
Conflicts: blt-common, blt4.2, blt8.0, blt8.0-unoff
Description: the BLT extension library for Tcl/Tk - run-time package
 BLT is a library of useful extensions for the Tcl language and the
 popular Tk graphical toolkit.  It adds a vector and tree data type,
 background execution and some debugging tools to Tcl, and provides
 several new widgets for Tk, including graphs, bar-charts, trees, tabs,
 splines and hyper-links, as well as a new geometry manager, drag &
 drop support, and more.
 .
 This package contains everything you need to use BLT with your Tcl/Tk
 scripts and Tcl/Tk-enabled apps.
 .
 Homepage: [http://blt.sourceforge.net/](http://blt.sourceforge.net/)
```

---

### Post by Partyboi2 on 2009-08-28
```
Depends: libc6 (>= 2.4), libx11-6, tcl8.5 (>= 8.5.0) **[COLOR=Red]| [/COLOR]**tcl8.4 (>= 8.4.16), tk8.5 (>= 8.5.0) | tk8.4 (>= 8.4.16)
```
Change the [COLOR=Red]**|**[/COLOR] to a ,

---

