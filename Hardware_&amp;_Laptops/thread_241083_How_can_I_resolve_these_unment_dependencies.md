---
title: "How can I resolve these unment dependencies?"
date: 2006-08-21
forum: Hardware &amp; Laptops
---

### Post by KennyL on 2006-08-21
I have been having a hell of a time installing linux-headers-686. While using apt-get the package was not available. So I started to install this myself however now I'm a mess. HOw can resolve these dependencies below?

kenny@earth:$ apt-get -f install
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied )
E: Unable to lock the list directory
kenny@a\earth:$ sudo apt-get install linux-header s-686
Password:
Reading package lists... Done
Building dependency tree... Done
linux-headers-686 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gcc-4.1: Depends: gcc-4.1-base (= 4.1.1-11) but it is not installable
           Depends: cpp-4.1 (= 4.1.1-11) but it is not installable
           Depends: binutils (>= 2.16.1cvs20051214) but 2.16.1-2ubuntu6 is to be  installed
           Depends: libgcc1 (>= 1:4.1.1-11) but 1:4.0.1-4ubuntu9 is to be instal led
           Depends: libssp0 but it is not installable
           Depends: libc6 (>= 2.3.6-6) but 2.3.5-1ubuntu12 is to be installed
  linux-headers-2.6.17-2-686: Depends: linux-kbuild-2.6.17 but it is not install able
  linux-headers-686: Depends: linux-headers-2.6.17-6-686 but it is not installab le
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s olution).

Any help is much appreciated.

Kenny

---

### Post by neko18 on 2006-08-21
Try:
```
sudo apt-get -f install
```

---

### Post by KennyL on 2006-08-22
Oops. Thanks

If you can comment, I'm trying to install linux-headers-686. However I keep getting this error.

kenny@earth:$ sudo apt-get linux-headers-686
E: Invalid operation linux-headers-686
kenny@tst-lowk-ssf:~$ sudo apt-get install linux-headers-686
Reading package lists... Done
Building dependency tree... Done
Package linux-headers-686 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-686 has no installation candidate

---

