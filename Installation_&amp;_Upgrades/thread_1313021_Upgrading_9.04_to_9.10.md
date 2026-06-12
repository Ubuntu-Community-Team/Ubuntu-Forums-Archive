---
title: "Upgrading 9.04 to 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Joshun on 2009-11-03
Hello at ubuntu forums. Please can you help me upgrade Ubuntu 9.04 (Jaunty) to Ubuntu 9.10. When I tried to upgrade it, it got this error::(
> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
Can not mark 'ubuntu-desktop' for upgrade

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.   

I also attached a screenshot and the dist-upgrade logs
Please help

Joshun

---

### Post by mikewhatever on 2009-11-03
Do you think any of the causes apply? Have you installed any software that's not from the repositories, or removed packages from the default installation? Can you post the output of the following command from a Terminal:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Joshun on 2009-11-03
I already had the Ubuntu-Desktop package installed. 
Here is the terminal output:

> oleary@oleary-desktop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for oleary: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
oleary@oleary-desktop:~$

This is what happened when I tried to upgrade from terminal:

> oleary@oleary-desktop:~$ do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tools 
Done downloading            
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg' 
[sudo] password for oleary: 

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty Release.gpg
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-updates Release.gpg
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-security Release.gpg
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-backports Release.gpg
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty Release
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-updates Release
Done [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty Release
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-security Release
Done [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-updates Release
Done [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-security Release
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-backports Release
Done [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-backports Release
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty/main Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty/restricted Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty/main Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty/restricted Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty/universe Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty/universe Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty/multiverse Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty/multiverse Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-updates/main Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-updates/restricted Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-updates/main Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-updates/restricted Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-updates/universe Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-updates/universe Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-updates/multiverse Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-updates/multiverse Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-security/main Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-security/restricted Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-security/main Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-security/restricted Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-security/universe Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-security/universe Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-security/multiverse Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-security/multiverse Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-backports/restricted Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-backports/main Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-backports/multiverse Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) jaunty-backports/universe Packages
Done downloading            
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Updating repository information
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic Release.gpg
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-updates Release.gpg
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-security Release.gpg
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-backports Release.gpg
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic Release
Done [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic Release
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-updates Release
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-security Release
Done [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-updates Release
Done [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-security Release
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-backports Release
Done [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-backports Release
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic/main Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic/restricted Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic/main Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic/restricted Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic/universe Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic/universe Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic/multiverse Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic/multiverse Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-updates/main Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-updates/restricted Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-updates/main Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-updates/restricted Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-updates/universe Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-updates/universe Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-updates/multiverse Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-updates/multiverse Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-security/main Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-security/restricted Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-security/main Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-security/restricted Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-security/universe Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-security/universe Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-security/multiverse Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-security/multiverse Sources
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-backports/restricted Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-backports/main Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-backports/multiverse Packages
Hit [http://ftp.ticklers.org](http://ftp.ticklers.org) karmic-backports/universe Packages
Done downloading            

Checking package manager
Reading package lists: Donemic-backports/universe Packages: 92    
Reading state information: Done
Reading state information: Done
Reading state information: Done

Calculating the changes

Support for some applications ended 

Canonical Ltd. no longer provides support for the following software 
packages. You can still get support from the community. 

If you have not enabled community maintained software (universe), 
these packages will be suggested for removal at the end of the 
upgrade. 

Demoted: 
acl, binutils-static, bluez-gnome, contact-lookup-applet, cpp-4.3, 
cupsddk, epiphany-browser, epiphany-browser-data, 
epiphany-browser-dbg, epiphany-extensions, epiphany-gecko, g++-4.3, 
gcc-4.3, gcc-4.3-base, gcj-4.3-base, gfortran-4.3, gij-4.3, 
gnome-mount, gnome-user-guide-en, gstreamer0.10-gnomevfs, 
human-icon-theme, kino, klogd, libares0, libgcj9-0, libgcj9-0-awt, 
libgcj9-jar, libglew1.5, libgnome-speech7, libgnomevfs2-bin, 
libitext-java, libmono-data1.0-cil, libmono-data2.0-cil, 
libmono-getoptions1.0-cil, libmono-posix1.0-cil, libmysqlclient15off, 
libpolkit-gnome0, libsmbios2, libstdc++6-4.3-dev, libstdc++6-4.3-pic, 
nvidia-180-modaliases, openoffice.org-writer2latex, phonon, 
pidgin-otr, policykit-gnome, python-clientform, python-gdata, 
python-launchpad-bugs, python-mechanize, python-twisted-web2, 
python-usb, rss-glx, sysklogd, tangerine-icon-theme, 
ttf-kochi-gothic, ttf-sazanami-gothic, ubuntu-gdm-themes, 
w3c-dtd-xhtml 



Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
Can not mark 'ubuntu-desktop' for upgrade 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


Restoring original system state

Aborting
Reading package lists: Donenty-backports/universe Packages: 92    
Reading state information: Done
Reading state information: Done
Reading state information: Done

---

### Post by snowpine on 2009-11-03
Hi Joshun, I always recommend a fresh install (rather than upgrading). It is just much simpler on so many levels.

I'm not sure what ticklers.org is, but try using one of the official canonical mirrors instead.

---

### Post by Joshun on 2009-11-03
Ticklers.org an up to date server according to the launchpad statistics. I have found it faster than the Canonical servers - when the canonical servers are busy I have found them to run a bit slow.

---

### Post by Joshun on 2009-11-03
I changed the server to archive.ubuntu.com but it didn't make any difference.

---

### Post by witeshark17 on 2009-11-03
I have not seen this clarified anywhere after searching: has the better result been by using the GUI update manager *upgrade* button or by downloading the upgrade in terminal?

---

### Post by Joshun on 2009-11-04
Both of the terminal and the upgrade-manager gui give exactly the same error message and log: could not mark ubuntu-desktop...

---

### Post by xiao_wen on 2009-11-04
I did have this message and issue after I change my default /usr/bin/python to python3.1 instead of python2.6.

I changed back default to python2.6, problem is gone.

hope this help,

keivn

---

### Post by Joshun on 2009-11-06
I've tried adjusting the python version but it doesn't make any difference.

---

