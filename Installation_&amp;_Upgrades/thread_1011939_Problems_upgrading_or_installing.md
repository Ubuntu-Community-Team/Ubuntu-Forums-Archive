---
title: "Problems upgrading or installing"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by itd on 2008-12-15
Hi,
recently I updated linux to get rid of some problems, I already had.
The upgrade went fine, except one thing. Two applications were not updated, because there were errors. 
Now everything works, except that I cannot install new applications.
For example, I tried to install sun-java6-jdk.
Here is the result :
```

Reading package lists... Done                       
Building dependency tree                            
Reading state information... Done                   
The following packages were automatically installed and are no longer required:
  libopenal0a python-pexpect libdc1394-13 mplayer-skins python-twisted-web     
  libsvga1 g++-4.2 python-pycurl libxerces-c28 libxalan110 libglide2           
  libavformat1d libx264-57 libenca0 libggi2 oss-compat libgii1 libxml1         
  libgii1-target-x libstdc++6-4.2-dev libavcodec1d python-smartpm libxerces27  
  libmotif3                                                                    
Use 'apt-get autoremove' to remove them.
Suggested packages:
  sun-java6-demo sun-java6-doc sun-java6-source
The following NEW packages will be installed:
  sun-java6-jdk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 17.5MB of archives.
After this operation, 56.0MB of additional disk space will be used.
Get:1 http://si.archive.ubuntu.com intrepid/multiverse sun-java6-jdk 6-10-0ubuntu2 [17.5MB]
Fetched 17.5MB in 11s (1561kB/s)
Preconfiguring packages ...
Selecting previously deselected package sun-java6-jdk.
(Reading database ... 134346 files and directories currently installed.)
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6-10-0ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Setting up at (3.1.10.1ubuntu3) ...
 * Starting deferred execution scheduler atdinvoke-rc.d: initscript atd, action "start" failed.
dpkg: error processing at (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on at; however:
  Package at is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up sun-java6-jdk (6-10-0ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.

Errors were encountered while processing:
 at
 ubuntu-standard


```

The last two applications are the ones, that couldn't be updated.
I also can't install them manually, because I get the same error as above.
Can anyone help??
PS: I am new in Linux (almost totaly noob ;) )

---

### Post by itd on 2008-12-16
Can't anyone help??
please :(

---

