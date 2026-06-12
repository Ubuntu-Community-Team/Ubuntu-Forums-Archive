---
title: "Failed Dependancies"
date: 2008-09-15
forum: General Help
---

### Post by CarlosinFL on 2008-09-15
I have 8.04 running and we purchased a APC appliance that has software I need to install...

[http://updates.netbotz.com/NetBotzV2/2.2/install.htm](http://updates.netbotz.com/NetBotzV2/2.2/install.htm)

Now when I run the commands as they indicate, I get the following errors:

```
root@tunafish:/tmp# sh ./install.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.4159/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

```

Anyone know how I can resolve this error?

---

### Post by Pro-reason on 2008-09-15
Simply go into Synaptic and look for packages with names like “libc”, “librt”, etc.  Try to satisfy the dependencies.  Then try again.

---

### Post by Bad Penguin on 2008-10-26
> **Pro-reason said:**
> Simply go into Synaptic and look for packages with names like “libc”, “librt”, etc.  Try to satisfy the dependencies.  Then try again.

Er, if libc was not installed, he wouldn't even be booted up.

I am experiencing the same problem and I can assure you, libc.so.6 is installed, along will all of the other "missing" libs the netbotz installer is complaining about.  

Something is wrong with the netbotz installer, not ubuntu.

---

### Post by Pro-reason on 2008-10-26
> **Bad Penguin said:**
> Er, if libc was not installed, he wouldn't even be booted up.

But perhaps the *-dev* version of the package is required?

I don't know; I haven't tried.  No doubt you're right.

---

