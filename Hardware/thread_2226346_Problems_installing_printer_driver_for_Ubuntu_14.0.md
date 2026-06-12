---
title: "Problems installing printer driver for Ubuntu 14.04"
date: 2014-05-26
forum: Hardware
---

### Post by archp2009 on 2014-05-26
I get this error in the final step:  How do I work around this problem installing driver for MP520 printer on Ubuntu 14.04?

The following packages have unmet dependencies:
 cnijfilter-mp520series:i386 : Depends: libtiff4:i386 (> 3.9.5-3~) but it is not installable
E: Unable to correct problems, you have held broken packages.

I was following this guide:  [http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mp-series-on-ubuntu-14-04-trusty-tahr-linux-mint-17-qiana-and-their-derivative-systems/](http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mp-series-on-ubuntu-14-04-trusty-tahr-linux-mint-17-qiana-and-their-derivative-systems/)

---

### Post by archp2009 on 2014-05-26
I reinstalled  libtiff4:i386 using Ubuntu software center.  It detected that a file being used by a Photo Editor called Lightworks needed to be removed.  Now the printer software installs properly and works.

---

### Post by archp2009 on 2014-05-26
I thought I had this problem figured out, but when testing it on other variations of Ubuntu it keeps happening again.  I am in Kubuntu 14.04 now and I keep getting:

2014-05-26 22:12:28 (212 KB/s) - ‘libtiff4_3.9.7-2ubuntu1_amd64.deb.11’ saved [147442/147442]

arch@arch-System-Product-Name:~$ sudo dpkg -i libtiff4_3.9.7-2ubuntu1_amd64.deb
[sudo] password for arch: 
Selecting previously unselected package libtiff4:amd64.
(Reading database ... 198835 files and directories currently installed.)
Preparing to unpack libtiff4_3.9.7-2ubuntu1_amd64.deb ...
Unpacking libtiff4:amd64 (3.9.7-2ubuntu1) ...
Setting up libtiff4:amd64 (3.9.7-2ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
arch@arch-System-Product-Name:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
arch@arch-System-Product-Name:~$ sudo apt-get install cnijfilter-mp520series
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 cnijfilter-mp520series:i386 : Depends: libtiff4:i386 (> 3.9.5-3~) but it is not installable
E: Unable to correct problems, you have held broken packages.
arch@arch-System-Product-Name:~$

---

### Post by archp2009 on 2014-05-27
In Kubuntu all I had to do was to go into System Settings ... Printers ... add printer.  The printer was listed and installed from there.

---

