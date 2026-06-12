---
title: "Printer Driver Issues - Corrupted Package - Brother MFC8440 printer"
date: 2009-06-14
forum: Hardware
---

### Post by seattlelinuxguy on 2009-06-14
Hello,

I'm currently having issues with a driver I installed for my Brother MFC-8440 printer.  I went to install the driver by getting the .deb package from Brother's website (I had no idea until after I messed everything up that I could have just gotten it via apt-get but oh well live and learn) and after installing it it's now causing problems with my machine.  I can print just fine but it's causing problems with my installation manager.  I ran sudo apt-get check and got the following message:

matt@matt-desktop:~/Documents/Brother MFC-8440 Linux Drivers$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc8440lpr needs to be reinstalled, but I can't find an archive for it.


The thing is that I can get this driver via apt-get but when I do I get the following:

matt@matt-desktop:~/Documents/Brother MFC-8440 Linux Drivers$ sudo apt-get install mfc8440lpr 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc8440lpr needs to be reinstalled, but I can't find an archive for it.

When I check to see if the package is installed, it says it s as shown here:

matt@matt-desktop:~/Documents/Brother MFC-8440 Linux Drivers$ dpkg  -l  |  grep  Brother
ii  brscan                                     0.2.4                                   Brother CUPS Printer Definitions
ii  cupswrappermfc8440                         1.0.2-1                                 Brother MFC8440 CUPS wrapper driver
rHR mfc8440lpr                                 1.1.2-1                                 Brother lpr Printer Definitions

I've also tried reinstalling the archive via dpkg as per Brother's instructions:
[http://solutions.brother.com/linux/en_us/instruction_prn3.html](http://solutions.brother.com/linux/en_us/instruction_prn3.html)
All I get is the same 'needs to be reinstalled but I just end up getting this:

matt@matt-desktop:~/Documents/Brother MFC-8440 Linux Drivers$ sudo dpkg -i --force-all --force-architecture mfc8440lpr-1.1.2-1.i386.deb
Selecting previously deselected package mfc8440lpr.
(Reading database ... 125972 files and directories currently installed.)
Preparing to replace mfc8440lpr 1.1.2-1 (using mfc8440lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc8440lpr ...
/var/lib/dpkg/info/mfc8440lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc8440lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8440lpr-1.1.2-1.i386.deb


I've read the man page for dpkg and have tried using several other flags along with dpkg to get this corrupted package removed and this is what I got:

matt@matt-desktop:~/Documents/Brother MFC-8440 Linux Drivers$ sudo dpkg -P --force-all --force-architecture mfc8440lpr
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 125971 files and directories currently installed.)
Removing mfc8440lpr ...
/var/lib/dpkg/info/mfc8440lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc8440lpr (--purge):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8440lpr

matt@matt-desktop:~/Documents/Brother MFC-8440 Linux Drivers$ sudo dpkg -r --force-all --force-architecture mfc8440lpr
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 125971 files and directories currently installed.)
Removing mfc8440lpr ...
/var/lib/dpkg/info/mfc8440lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc8440lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8440lpr

matt@matt-desktop:~/Documents/Brother MFC-8440 Linux Drivers$ sudo dpkg -i --force-all --force-architecture mfc8440lpr
dpkg: error processing mfc8440lpr (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc8440lpr


So what I'm wondering here is how do I tell Ubuntu where the archive is?  What is Ubuntu missing here?  I'm stuck in this gray area where the package is messed up but I can't find a way to reinstall it or remove it.  I noticed in some of the error messages above that it appears that some of the files that dpkg needs to remove the driver can't be found for one reason or another.  My guess is that this is part of the reason that I'm having issues.  I'm not sure where to go from here though.  Any help will be greatly appreciated as this package conflict is currently keeping me from updating properly.

---

### Post by LCollins on 2009-08-10
I understand your pain - I have the exact same problem to.

---

### Post by rogerw05465 on 2009-08-16
I had this same issue with a mfc6800 driver, and it messed up my Synaptics. I tried all sorts of stuff. Though I still do not have a working printer, this is what I did to clear out the mess:
    sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.backup
    sudo apt-get update

After running apt-get updates, I got an error that there was no status file
- I copied the status.backup to status, and of course had my original problem back
- I edited the status file and removed the section on the package I was having problems with, then saved it
&#8226; Presto Chango, Synaptic works again!
So, look in the status file and remove the section you find by searching on MFC8440

---

### Post by Vincent R on 2009-09-19
I did have the same problem with my mfc9660 printer. By removing the paragraph from the status file I finally got the Synaptic package manager running again (and a working printer). 

Thanks.

---

