---
title: "LanSafe 6.0.3.1 for Linux does not install on Ubuntu 10.04"
date: 2010-07-28
forum: Hardware
---

### Post by CeeAdm on 2010-07-28
I downloaded the latest version (as of 7/28/2010) of LanSafe from Powerware's website. I've tried both the LS_603_linux_el4.tar package and the LS_603_linux.tar package with the same results. Here's the transcript...
 
 
*****@*****:/usr/src/LanSafe_el4$ sudo ./install.sh
 
-----------------------------------------------------------------
EATON | Powerware
Welcome to LanSafe!
Version 6.0.3
To install LanSafe for LINUX/UNIX, press y and then press <ENTER>
and fill in the configuration items as they are presented to you.
-----------------------------------------------------------------
 
Continue installation? (y/n) [y] y
 
Installing from CD-ROM
 
The default install path name for this software is:
/usr/Powerware/LanSafe
Do you want to continue with this install path? (y/n) [y] n
Enter absolute install path: /opt/Powerware/LanSafe
New install path is: /opt/Powerware/LanSafe
Is this okay? (y/n) [y]
 
---------------------------------------------------------------
LanSafe Installation Parameters:
File to install from : CD_ROM
Directory to install to : /opt/Powerware/LanSafe
---------------------------------------------------------------
 
Are these installation parameters acceptable? (y/n) y
License Agreement:
 
Eaton Corporation
END-USER LICENSE AGREEMENT
 
Revised: May, 2008
 
IMPORTANT, READ CAREFULLY. THIS EATON CORPORATION END USER
LICENSE AGREEMENT (THE "AGREEMENT") IS A BINDING CONTRACT
BETWEEN YOU, THE END-USER (THE "LICENSEE") AND EATON
CORPORATION ("EATON" OR "LICENSOR"). EXCEPT TO THE EXTENT
YOU ARE BOUND BY A WRITTEN AGREEMENT SIGNED BY BOTH YOU AND
EATON REGARDING THE USE AND LICENSE OF THIS SOFTWARE
PRODUCT, BY INSTALLING OR USING THIS SOFTWARE PRODUCT, YOU,
THE LICENSEE, ARE AGREEING TO BE BOUND BY THE TERMS,
CONDITIONS AND LIMITATIONS OF THIS AGREEMENT, WHICH
INCLUDES, BUT IS NOT LIMITED TO, THE SOFTWARE USAGE LICENSE,
THE DISCLAIMER OF WARRANTY AND LIMITED WARRANTY, AND
Press <ENTER> to continue, (1) to skip to the end, or (0) to cancel: 1
Do you accept all terms of the preceding license Agreement?
If you do not accept the terms, then the Setup will close.
To install LanSafe, you must accept this agreement.
1. I accept.
0. I do not accept.
Enter selection: 1
Installing PowerMonitor.email to /opt/Powerware/LanSafe/Bin ...done
Installing PowerMonitor.broadcast to /opt/Powerware/LanSafe/Bin ...done
Installing PowerMonitor.shutdown to /opt/Powerware/LanSafe/Bin ...done
Installing PowerMonitor.unload to /opt/Powerware/LanSafe/Bin ...done
Installing PowerMonitor.sh to /opt/Powerware/LanSafe/Bin ...done
Installing upslist.ups to /opt/Powerware/LanSafe/Config ...done
Installing PowerMonitorEvents.def to /opt/Powerware/LanSafe/Config ...done
Installing install.ls to /opt/Powerware/LanSafe/Bin ...done
Installing install.txt to /opt/Powerware/LanSafe/Bin ...done
Installing PowerMonitorC to /opt/Powerware/LanSafe/Bin ...done
Installing PowerMonitorM to /opt/Powerware/LanSafe/Bin ...done
Installing PowerMonitorX to /opt/Powerware/LanSafe/Bin ...done
Installing PowerMonitorIcon to /opt/Powerware/LanSafe/Bin ...done
Installing uninstall.sh to /opt/Powerware/LanSafe/Bin ...done
Installing OEMModel.ini to /opt/Powerware/LanSafe/Bin ...done
Installing license.txt to /opt/Powerware/LanSafe ...done
Adding PowerMonitor services in /etc/services.
sysv_startatboot
Ready to copy ls.init to install path
Installing ls.init to init.d ...done
Deleting /etc/rc2.d/S89ls.init
Deleting /etc/rc5.d/S89ls.init
Linking /etc/rc2.d/S89ls.init to /etc/init.d/ls.init ...
Linking /etc/rc5.d/S89ls.init to /etc/init.d/ls.init ... done
Deleting /etc/rc0.d/K89ls.init
Linking /etc/rc0.d/K89ls.init to /etc/init.d/ls.init ... done
 
 
==========================================================================
Welcome to LanSafe for LINUX/UNIX 6.0.3.1
==========================================================================
install.ls: relocation error: /lib/tls/i686/cmov/libresolv.so.2: symbol memcpy, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
---------------------------------------------------------------
/opt/Powerware/LanSafe/Bin/PowerMonitor.sh: 19: ./PowerMonitor: not found
LanSafe was successfully installed on your system.
---------------------------------------------------------------
 
Registration:
Please go to [www.powerware.com]("http://www.powerware.com") to register LanSafe.
*****@*****:/usr/src/LanSafe_el4$
 
 
The everything appears to work fine until you get to the last part under "Welcome to LanSafe..." where it mentions the relocation error. I've also tried this using the default target directory instead of my preferred directory, but the problem still persists.
 
If I try to run the init script I get the following transcript...
 
 
*****@*****:/etc/init.d$ sudo ./ls.init start
*****@*****:/etc/init.d$ sudo ./ls.init stop
PowerMonitor (LanSafe Power Monitor) stopped
*****@*****:/etc/init.d$
 
 
Essentially nothing happens when I run start. Nothing shows up in ps -A at least. And I assume the stop message echos even if the process was non-existant.
 
Anyone using LanSafe successfully on Ubuntu Lucid?

---

### Post by gready on 2010-07-28
I have the same problem

Try this I did and it seems to install haven't tried running it yet as my ups is not connected at the moment

sudo apt-get install nscd
# open /etc/nscd.conf with your $EDITOR
# find following line:
#         enable-cache            hosts           no
# change "no" to "yes"
# save & exit the editor
sudo service nscd restart

---

### Post by staceygeek on 2011-07-14
Hi,

run the following commands:

sudo rm /lib/tls/i686/cmov/libc.so.6
sudo ln -s /lib/libc-2.11.1.so /lib/tls/i686/cmov/libc.so.6

so you will get rid of your error with libc.so.6, namely:

install.ls: relocation error: /lib/tls/i686/cmov/libresolv.so.2: symbol  memcpy, version GLIBC_2.0 not defined in file libc.so.6 with link time  reference

---

