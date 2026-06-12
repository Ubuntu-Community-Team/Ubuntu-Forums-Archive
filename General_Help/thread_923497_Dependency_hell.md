---
title: "Dependency hell"
date: 2008-09-18
forum: General Help
---

### Post by timothius on 2008-09-18
Hi,

I am trying to install a library I need to build a package:

```
$ sudo apt-get install libdbus-glib-1-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libdbus-glib-1-dev: Depends: libdbus-glib-1-2 (= 0.74-2) but 0.74-4~804.nm1 is to be installed
E: Broken packages
```

I have no idea how to fix the above error.  Does anyone have any ideas?

I'm running the 64bit version of Hardy. 

Thanks,

T

---

### Post by ju2wheels on 2008-09-18
Are you installing a 32bit lib on 64bit Ubuntu? getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by timothius on 2008-09-18
Nope, the library is a 64bit library.

```
$ apt-cache showpkg libdbus-glib-1-dev 
Package: libdbus-glib-1-dev
Versions: 
0.74-2 (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-amd64_Packages
                  MD5: 5ea06bb77132d80541f7a3ebc3402f7a


```

---

### Post by cdenley on 2008-09-18
It looks like you installed a package which was not from the ubuntu repository, which is now causing you conflicts because it is newer than the package you are now trying to install.
```

sudo dpkg -P libdbus-glib-1-2

```
Make sure you DO NOT have this repo configured
[https://launchpad.net/~dalbers/+archive](https://launchpad.net/~dalbers/+archive)
and don't install things like this
[https://launchpad.net/~dalbers/+archive/+build/639946](https://launchpad.net/~dalbers/+archive/+build/639946)

---

