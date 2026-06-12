---
title: "Problem with Update Manager, any help much appreciated!!"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by docus on 2009-05-06
Hello, I'm having a problem installing updates on Ubuntu 9.04.  Things have been going OK until now.  By the look of it there's something wrong with Update Manager and Update Manager Core, but I don't have any idea what to do about it?  Also something about Python???  Any help would be much appreciated!

Here's a cut 'n paste of sudo apt-get and sudo apt-get install -f :



docus@Stinkpad:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_GB                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources
Reading package lists... Done
docus@Stinkpad:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up update-manager-core (1:0.111.9) ...
Compiling /usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeCache.py ...
Sorry: IndentationError: ('unindent does not match any outer indentation level', ('/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeCache.py', 888, 28, '                  iforeign:\n'))
pycentral: pycentral pkginstall: error byte-compiling files (49)
pycentral pkginstall: error byte-compiling files (49)
dpkg: error processing update-manager-core (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.111.9); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 update-manager-core
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Tobi-fp on 2009-05-06
try doing sudo apt-get update --fix-missing

---

