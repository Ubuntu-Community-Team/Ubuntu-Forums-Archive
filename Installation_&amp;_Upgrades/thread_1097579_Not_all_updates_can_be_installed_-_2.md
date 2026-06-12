---
title: "Not all updates can be installed - 2"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by james.wilde on 2009-03-16
Above is the heading in a window which opens when I click on the update button.  Something I've tried to install didn't go all the way, maybe or maybe it's an unofficial Ubuntu package.

Is there any command which will tell me what package it is that is faulty, and maybe another command that will force its removal?

TIA

//James

---

### Post by james.wilde on 2009-03-16
Never mind - managed to fix it.  Sorry.

---

### Post by Oli4 on 2009-05-12
Hi James,
What did you do to fix your problem?  I'm sitting with the same issue.

Please help!

Thanks
Nico

---

### Post by Partyboi2 on 2009-05-12
> **Oli4 said:**
> Hi James,
What did you do to fix your problem?  I'm sitting with the same issue.

Please help!

Thanks
Nico
Hi Oli4, not sure how long before James will respond but maybe someone else can help you, can you open a terminal and  post the output to
```
sudo apt-get -f install
sudo dpkg --configure -a

```

---

### Post by Oli4 on 2009-05-13
Partyboi2,

Thanks for the reply...

Here is the output you asked for:
> 
nico@server1:~$ sudo apt-get -f install
[sudo] password for nico: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
nico@server1:~$ sudo dpkg --configure -a
nico@server1:~$ 


Thanks in advance for any help/assistance you can give me.

---

### Post by Partyboi2 on 2009-05-13
> **Oli4 said:**
> Partyboi2,

Thanks for the reply...

Here is the output you asked for:


Thanks in advance for any help/assistance you can give me.
Those outputs do not show any problems. 
What is the output to
```
sudo apt-get update
sudo apt-get upgrade
```
Is there any further information you can provide?

---

### Post by Oli4 on 2009-05-13
Partyboi2,

I solved the problem.

Here is the output of those commands you gave me:
> 
nico@server1:~$ **sudo apt-get update**
[sudo] password for nico: 
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable Release.gpg                                 
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main Translation-en_AU                      
.
.
.
.
.
Get:16 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Packages [196kB]    
Fetched 1207kB in 12s (94.6kB/s)                                               
Reading package lists... Done
nico@server1:~$ **sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  clamav clamav-freshclam linux-generic linux-headers-generic
  linux-image-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
nico@server1:~$ 


I removed all clamav software, and update manager completed without problem.  I owe you :popcorn::popcorn:

Why does this happen?

Thanks,
Nico

---

### Post by simgriff on 2009-05-24
I have the same "Not all updates can be installed" and "Could not calculate upgrade" error messages.
The results of sudo apt-get update is:

Fetched 310B in 32s (10B/s)                                                    
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: You may want to run apt-get update to correct these problems

The results of sudo apt-get upgrade is:

The following packages have been kept back:
  openoffice.org openoffice.org-base openoffice.org-base-core
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-filter-binfilter openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-math
  openoffice.org-officebean openoffice.org-report-builder-bin
  openoffice.org-style-andromeda openoffice.org-style-crystal
  openoffice.org-style-human openoffice.org-style-tango openoffice.org-writer
  python-uno uno-libs3 ure
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.

I don't understand any of this - are you able to help me????

simgriff
eeepc 900 running eeebuntu 2.0 standard

---

