---
title: "Is there an easy way to install some latest software version?"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by hansyin on 2009-06-16
Hi,

I already updated my ubuntu to 9.04. Now I need to use the latest openswan version, like 2.6.21.  From the "synaptic package manger" I can only get version 2.4.12.  Is there an easy way to update it?
I know I can download the latest software tarball to install it, but it need to be compiled by myself, and it's not easy to remove it when I don't like it.

Similar problem also exist for many other software.  Can somebody give me an idea? 

Thanks in advance. 


Hans

---

### Post by Lean 946 on 2009-06-16
Basically:
```
sudo apt-get remove openswan
```
to remove the package.
Then, you download the latest version, and do this:
```
sudo apt-get build-dep openswan
```
That would install all the dependencies as well header files.
Now you can proceed easily to compile:
```
./configure
make
sudo make install
```
To erase:
```
sudo make uninstall
``` 
I hope that it helps.

---

### Post by Shazaam on 2009-06-16
And if you install checkinstall you can make a .deb of the app. From the info in Synaptic...
```
installation tracker
CheckInstall keeps track of all the files created or
modified by your installation script ("make install"
"make install_modules", "setup", etc), builds a
standard binary package and installs it in your
system giving you the ability to uninstall it with your
distribution's standard package management utilities.

```
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by Lean 946 on 2009-06-17
I add something to myself: instead of getting the tarballs, you could get the svn (or cvs, or git, or bazaar) version of the app. And, of course, make a .deb with checkinstall.

---

