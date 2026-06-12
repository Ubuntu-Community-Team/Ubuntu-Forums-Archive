---
title: "[SOLVED] Unable to install Yahoo! Zimbra Desktop"
date: 2008-09-29
forum: General Help
---

### Post by x1a4 on 2008-09-29
Hi,

I'm unable to install the zdesktop package on Hardy.  I'm using Aptitude and my output is as follows:
```

~/% sudo -i
~/# aptitude install zdesktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  zdesktop [0.90.1249beta-hardy1] 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/51.5MB of archives. After unpacking 51.4MB will be used.
Writing extended state information... Done
Selecting previously deselected package zdesktop.
(Reading database ... 285014 files and directories currently installed.)
Unpacking zdesktop (from .../zdesktop_0.90.1249beta-hardy1_i386.deb) ...
Setting up zdesktop (0.90.1249beta-hardy1) ...
hex1a4 is not in the sudoers file.  This incident will be reported.
dpkg: error processing zdesktop (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 zdesktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up zdesktop (0.90.1249beta-hardy1) ...
hex1a4 is not in the sudoers file.  This incident will be reported.
dpkg: error processing zdesktop (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 zdesktop
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Exit 255
~/# 

```
I am in the sudoers file as well as the admin group.

Anything I can do to fix this, or is this an issue with the package and/or repo?

Thank you.

---

### Post by Sef on 2008-09-29
Moved to general help.

---

### Post by x1a4 on 2008-09-30
I think the problem was with the post-install script not able to run the Zimbra installer.  The zdesktop installation did install all the required files, I ran the installer myself from my user account instead of as root and was able to install Zimbra.  I than removed the zdesktop package and all is well.

---

