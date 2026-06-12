---
title: "ClamAV Installation/Usage Issues"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by mangellinux on 2009-08-22
Hello all,  I'm new to linux, and I wanted virus protection for this system and for transfer with Windows systems. I was reading here that ClamAV is preinstalled on Ubuntu 9.04. So I used the Add/Remove program to get the GUI for ClamAV called "Virus Scanner". It says it has no definitions and that the GUI needs an update, but it can't seem to do either of those. So I thought that ClamAV might come with the system but not be installed. So I searched the web and found code to installed it. It still doesn't work. Below is the code that the terminal spat out.  NOTE: I edited out my name with "XXX"  XXX@XXX-desktop:~$ sudo aptitude install clamav clamav-daemon clamav-freshclam [sudo] password for XXX:  Reading package lists... Done Building dependency tree        Reading state information... Done Initializing package states... Done Writing extended state information... Done The following NEW packages will be installed:   clamav clamav-daemon clamav-freshclam  The following packages will be REMOVED:   libbit-vector-perl{u} libcarp-clan-perl{u}    libnumber-compare-perl{u}    libtext-glob-perl{u}    linux-headers-2.6.28-11{u}    linux-headers-2.6.28-11-generic{u}  0 packages upgraded, 3 newly installed, 6 to remove and 0 not upgraded. Need to get 367kB/922kB of archives. After unpacking 73.5MB will be freed. Do you want to continue? [Y/n/?] y Writing extended state information... Done Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main clamav-daemon 0.95.2+dfsg-4ubuntu1.1 [367kB] Fetched 367kB in 3s (109kB/s)          debconf: unable to initialize frontend: Dialog debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.) debconf: falling back to frontend: Readline Preconfiguring packages ... (Reading database ... 121814 files and directories currently installed.) Removing libbit-vector-perl ... Removing libcarp-clan-perl ... Removing libnumber-compare-perl ... Removing libtext-glob-perl ... Removing linux-headers-2.6.28-11-generic ... Removing linux-headers-2.6.28-11 ... Processing triggers for man-db ... Selecting previously deselected package clamav-freshclam. (Reading database ... 105462 files and directories currently installed.) Unpacking clamav-freshclam (from .../clamav-freshclam_0.95.2+dfsg-4ubuntu1.1_i386.deb) ... Selecting previously deselected package clamav. Unpacking clamav (from .../clamav_0.95.2+dfsg-4ubuntu1.1_i386.deb) ... Selecting previously deselected package clamav-daemon. Unpacking clamav-daemon (from .../clamav-daemon_0.95.2+dfsg-4ubuntu1.1_i386.deb) ... Processing triggers for man-db ... Setting up clamav-freshclam (0.95.2+dfsg-4ubuntu1.1) ... debconf: unable to initialize frontend: Dialog debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.) debconf: falling back to frontend: Readline Replacing config file /etc/clamav/freshclam.conf with new version Replacement succeeded for "/usr/bin/freshclam".  * Starting ClamAV virus database updater freshclam    [ OK ]   Setting up clamav (0.95.2+dfsg-4ubuntu1.1) ... Setting up clamav-daemon (0.95.2+dfsg-4ubuntu1.1) ... Replacement succeeded for "/usr/sbin/clamd".  * Starting ClamAV daemon clamd                               LibClamAV Error: cli_loaddb(): No supported database files found in /var/lib/clamav ERROR: Can't open file or directory                                                        [fail]  Reading package lists... Done              Building dependency tree        Reading state information... Done Reading extended state information        Initializing package states... Done Writing extended state information... Done  XXX@XXX-desktop:~$

---

### Post by running_rabbit07 on 2009-08-22
> **mangellinux said:**
> Hello all,  I'm new to linux, and I wanted virus protection for this system and for transfer with Windows systems. 

I was reading here that ClamAV is preinstalled on Ubuntu 9.04. So I used the Add/Remove program to get the GUI for ClamAV called "Virus Scanner". It says it has no definitions and that the GUI needs an update, but it can't seem to do either of those. So I thought that ClamAV might come with the system but not be installed. So I searched the web and found code to installed it. It still doesn't work. Below is the code that the terminal spat out.  NOTE: I edited out my name with "XXX"  

***@***-desktop:~$ sudo aptitude install clamav clamav-daemon clamav-freshclam [sudo] 
password for ***: 
Reading package lists... 
Done Building dependency tree        Reading state information... 
Done Initializing package states... 
Done Writing extended state information...
Done The following NEW packages will be installed:   clamav clamav-daemon clamav-freshclam  
The following packages will be REMOVED:   libbit-vector-perl{u} libcarp-clan-perl{u}    libnumber-compare-perl{u}    libtext-glob-perl{u}    linux-headers-2.6.28-11{u}    linux-headers-2.6.28-11-generic{u}
 0 packages upgraded, 3 newly installed, 6 to remove and 0 not upgraded. Need to get 367kB/922kB of archives. After unpacking 73.5MB will be freed. 
Do you want to continue? [Y/n/?] y 
Writing extended state information... 
 Setting up clamav-daemon (0.95.2+dfsg-4ubuntu1.1) ... 
Replacement succeeded for "/usr/sbin/clamd". 
 * Starting ClamAV daemon clamd                               LibClamAV Error: cli_loaddb(): 
No supported database files found in /var/lib/clamav ERROR: 
Can't open file or directory                                                        [fail]  Reading package lists... 
Done              Building dependency tree        Reading state information... 
Done Reading extended state information        Initializing package states... 
Done Writing extended state information... 
Done ***@***-desktop:~$

Made it a bit more legible.

When looking for a program the Add/Remove doesn't work well.

Go to System>Administration> Synaptic Package Manager and search ClamAV, check the box beside it and then the green apply arrow at the top.

---

