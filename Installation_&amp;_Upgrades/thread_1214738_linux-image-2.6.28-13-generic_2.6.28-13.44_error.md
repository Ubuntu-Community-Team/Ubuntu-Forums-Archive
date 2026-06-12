---
title: "linux-image-2.6.28-13-generic 2.6.28-13.44 error"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by AndyRoberts on 2009-07-16
Hi,

I seem to be having an issue with the above image - every time I update it seems to fail.  I have audited with dpkg -C and it suggests reinstallation, which I have done (both by cleaning the /var/cache/apt/archives/ and manually installing the package through Gdebi) but to no avail.

It is preventing me from upgrading other updates and being a general pain in the backside, so any help would be greatly appreciated.

There is no mention of 2.6.28-13 in the Grub menu or menu.lst and there isn't a vmlinuz file in /boot/ of that image.

When I run apt-get update / apt-get install I get the following:

/bin/sh: /usr/sbin/dpkg-preconfigure: Permission denied
(Reading database ... 117886 files and directories currently installed.)
Preparing to replace linux-image-2.6.28-13-generic 2.6.28-13.44 (using .../linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb) ...
dpkg (subprocess): unable to execute new pre-installation script: Permission denied
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
andy@andy-laptop:~$ 


Any ideas please?

---

### Post by ptn107 on 2009-07-16
Make sure you prefix apt-get with 'sudo'.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by AndyRoberts on 2009-07-16
I had been running as root.  No difference.

---

### Post by ptn107 on 2009-07-16
It seems to be complaining about permissions, but if you indeed ran apt-get with root privileges then there shouldn't be a problem.  Maybe the dpkg database is screwed up.  Try adding the '-f' option?

```
sudo apt-get -f install linux-image-2.6.28-13-generic -y
```

---

### Post by AndyRoberts on 2009-07-17
No, I am afraid that still doesn't work.  I had tried the -f option in the dpkg interface as well and running an install through dpkg, no joy there either.  Tried purging, no joy, --configure -a, no help, 'Computer Janitor' gets stuck too.

Thanks for your help, though, I think I have probably exhausted all the available simple things.  Unless somebody has fixed the problem themselves it is going to be a fresh install for me this weekend.

I am still getting:

Preparing to replace linux-image-2.6.28-13-generic 2.6.28-13.44 (using .../linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb) ...
dpkg (subprocess): unable to execute new pre-installation script: Permission denied
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
------------------------------------------------------------------------



I guess that because it is halting all the other upgrades there is basically no chance any future packages can fix it, I'll have to reformat and start from scratch.

Rather not, though!

Thanks again.

---

