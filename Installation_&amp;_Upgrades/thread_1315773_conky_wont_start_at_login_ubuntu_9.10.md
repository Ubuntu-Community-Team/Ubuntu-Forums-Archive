---
title: "conky wont start at login ubuntu 9.10"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by zenxi on 2009-11-05
Conky is refusing to start at login, i tried adding just the command into system > admin > startup applications but it was ignored.  after that i tried sleep 30 && conky and it was still didnt start.  i didnt find any error messages under bootstrap.log, nor crash reports in apport.log  could it be that ubuntu is ignoring it?

---

### Post by Pablo Pablovski on 2009-11-05
What output do you get if you enter "conky &" in a terminal window?

---

### Post by felixnine on 2009-11-05
i had this problem as well because i wasn't running it in windowed mode, which you have to do with nautilus (apologies if you know this already).

conky starts with gnome for me, but it'll just disappear randomly and i have to restart it.

---

### Post by swartzer on 2009-11-18
I am having the same problem since upgrading to 9.10.  In the console it says:

conky: error while loading shared libraries: libaudclient.so.1: cannot open shared object file: No such file or directory

Note that I have both libaudclient2 (which includes libaudclient.so.2 and libaudclient.so.2.0.0) and audacious-dev (which includes libaudclient.so) installed.  I don't want to recompile with audacious support removed.  

I have no experience working directly with shared libraries, so I don't know if it is safe to just google up a copy of libaudclient.so.1 and put it in /usr/lib, or if it has to be part of a package install, or what.

Edit: I have tried both conky-all and conky-std and get the same error with both.

Further edit:  I have solved the problem by getting a .deb of the libaudclient1 package at [https://launchpad.net/ubuntu/karmic/+package/libaudclient1](https://launchpad.net/ubuntu/karmic/+package/libaudclient1) -- note you will have to choose your architecture and download the appropriate version of the package.  If you don't know which to choose and you are on a machine from a mainstream vendor like Dell, try i386.  The gDebi installer will warn you if you are trying to install a package from the wrong architecture.  I hope this helps somebody.

---

