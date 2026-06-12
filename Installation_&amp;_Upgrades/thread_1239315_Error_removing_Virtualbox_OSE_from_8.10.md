---
title: "Error removing Virtualbox OSE from 8.10"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by alekons on 2009-08-13
Hello,

I am trying to uninstall completely the Virtual box OSE from 8.10 and i am getting the following error.

```

sudo aptitude remove virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  dkms{u} 
The following partially installed packages will be configured:
  virtualbox-ose 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 381kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 201515 files and directories currently installed.)
Removing dkms ...
Processing triggers for man-db ...
Setting up virtualbox-ose (2.0.4-dfsg-0ubuntu1) ...
/etc/init.d/virtualbox-ose: line 63: /etc/init.d/functions: No such file or directory
invoke-rc.d: initscript virtualbox-ose, action "start" failed.
dpkg: error processing virtualbox-ose (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for menu ...
Errors were encountered while processing:
 virtualbox-ose
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

```

I have tried through synaptic also with no luck.


Thanks
Alexis

---

### Post by alekons on 2009-08-13
I just found out what the problem was. It's in this link:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/224836](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/224836)

I have a file in /etc called redhat-release. So when I was installing VBox it thought it was installing on redhat therefore it needed that functions file.
I created redhat-release file when I installed Oracle 11g a few months back 
I renamed the file and re-install VBox and everything is working fine.

Thanks a lot

---

