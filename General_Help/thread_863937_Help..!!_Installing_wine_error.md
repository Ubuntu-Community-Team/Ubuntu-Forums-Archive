---
title: "Help..!! Installing wine error????"
date: 2008-07-19
forum: General Help
---

### Post by ruzt on 2008-07-19
**When I install wine, i have problem with this bellow :**

[I]ruzt@ruzt:~$ sudo apt-get install wine
[sudo] password for ruzt: 
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

The following packages have unmet dependencies:
  wine: Depends: libldap2 (>= 2.1.17-1) but it is not installable
E: Broken packages
[/I]

[B]I try with command : 
[/B]
[I]ruzt@ruzt:~$ sudo aptitude install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  winbind 
The following NEW packages will be automatically installed:
  libaudio2 
The following NEW packages will be installed:
  libaudio2 wine 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 9725kB/9805kB of archives. After unpacking 61.2MB will be used.
The following packages have unmet dependencies:
  winbind: Depends: samba-common (= 3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.4 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
samba-common [3.0.28a-1ubuntu4.4 (now) -> 3.0.28a-1ubuntu4 (hardy)]
smbclient [3.0.28a-1ubuntu4.4 (now) -> 3.0.28a-1ubuntu4 (hardy)]

Score is 110

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  libaudio2 winbind 
The following packages will be DOWNGRADED:
  samba-common smbclient 
The following NEW packages will be installed:
  libaudio2 winbind wine 
0 packages upgraded, 3 newly installed, 2 downgraded, 0 to remove and 0 not upgraded.
Need to get 17.4MB/17.5MB of archives. After unpacking 61.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
ruzt@ruzt:~$ 
[/I]

Please help, i use hardy heron and haved update it..thank you!:confused:

---

### Post by pauper on 2008-07-19
It's likely that "wine" from repository is oudated, i.e. has some kind of
dependency conflict against current shared libraries on your system.

Follow instructions from here:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

