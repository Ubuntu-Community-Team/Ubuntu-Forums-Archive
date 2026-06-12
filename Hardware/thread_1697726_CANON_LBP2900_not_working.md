---
title: "CANON LBP2900 not working"
date: 2011-03-01
forum: Hardware
---

### Post by askrym on 2011-03-01
hello.

i have a problem getting my canon lbp2900 working , i tried to install it following this guide
[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

it's reported to work correctly on ubuntu 10.10 with the procedure explained on that webpage

i have tried the "automated install" process, i downloaded from the link provided the deb packages and the installing script.

[http://codebin.cotescu.com/canon/lbp_driver/CanonCAPTdriver.tar.gz](http://codebin.cotescu.com/canon/lbp_driver/CanonCAPTdriver.tar.gz)

then i have run the automated install script as su and provided my printer model LBP2900

i post here the output i got:

> paolo@paolo ~/Desktop/raducotescu-CanonCAPTdriver-0e79d06 $ sudo ./canonLBP_install.sh LBP2900
[sudo] password for paolo: 
Sorry, try again.
[sudo] password for paolo: 
Installing driver for model: LBP2900
using file: CNCUPSLBP2900CAPTK.ppd
Installing packages...
You do have the libstdc++6 package...
(Reading database ... 133416 files and directories currently installed.)
Preparing to replace libcupsys2 1.3.9-17ubuntu3.7 (using .../libcupsys2_1.3.9-17ubuntu3.7_all.deb) ...
Unpacking replacement libcupsys2 ...
Setting up libcupsys2 (1.3.9-17ubuntu3.7) ...
(Reading database ... 133416 files and directories currently installed.)
Preparing to replace cndrvcups-common 2.00-1 (using .../cndrvcups-common_2.00-1_amd64.deb) ...
Unpacking replacement cndrvcups-common ...
Setting up cndrvcups-common (2.00-1) ...
(Reading database ... 133416 files and directories currently installed.)
Preparing to replace cndrvcups-capt 2.00-1 (using .../cndrvcups-capt_2.00-1_amd64.deb) ...
Unpacking replacement cndrvcups-capt ...
Setting up cndrvcups-capt (2.00-1) ...
Processing triggers for ureadahead ...
Modifying the default /etc/init.d/ccpd file...
Restarting CUPS...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cups restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart cups
cups start/running, process 3611
Setting the printer for CUPS...
Setting the printer for CAPT...
/usr/sbin/ccpdadmin: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory
Setting CAPT to boot with the system...
update-rc.d: warning: /etc/init.d/ccpd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/ccpd ...
   /etc/rc0.d/K50ccpd -> ../init.d/ccpd
   /etc/rc1.d/K50ccpd -> ../init.d/ccpd
   /etc/rc6.d/K50ccpd -> ../init.d/ccpd
   /etc/rc2.d/S50ccpd -> ../init.d/ccpd
   /etc/rc3.d/S50ccpd -> ../init.d/ccpd
   /etc/rc4.d/S50ccpd -> ../init.d/ccpd
   /etc/rc5.d/S50ccpd -> ../init.d/ccpd
Starting ccpd...
 * Starting Canon Printer Daemon for CUPS: ccpd                                 /usr/sbin/ccpd: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory
                                                                         [fail]
Checking status:
Canon Printer Daemon for CUPS: ccpd:

Power on your printer! :)
Go to System - Administration - Printing and do the following:
  1. disable LBP2900-2 but do not delete it since Ubuntu will recreate it automatically;
  2. set LBP2900 as your default printer;
  3. reboot your machine and print a test page.
Script author: 
    Radu Cotescu
    [http://radu.cotescu.com](http://radu.cotescu.com)
paolo@paolo ~/Desktop/raducotescu-CanonCAPTdriver-0e79d06 $ 


my printer gets detected in the system->administration->printing

i enter printer proprieties and try to print a test page

> printer state: Idle - No %%BoundingBox: comment in header!

print self-test page:

> printer state: Processing

clean print heads

> printer state: Idle-Invalid printer command "Clean"!

I'd guess it depends on this

> Starting ccpd...
 * Starting Canon Printer Daemon for CUPS:  ccpd                                 /usr/sbin/ccpd: error while loading  shared libraries: libcups.so.2: cannot open shared object file: No such  file or directory
                                                                         [fail]
Checking status:
Canon Printer Daemon for CUPS: ccpd:

but... i honestly dont know how to fix this.
can someone kindly help me out please :) ?

---

### Post by prapanjganeshan on 2011-03-09
I assume you are trying this on amd64 (64 bit processor machine).

I was facing the same problem. I discovered that libcups.so.2 is a 32 bit library. So one needs to install ia32-libs for the 32 bits library that are essential for a 64 bit machine. 

You may find ia32-libs in synaptic package search. This help all issues I had regarding libcups.so.2

---

### Post by askrym on 2011-03-09
i forgot to write that sorry , i'm using maverick amd64.

i checked the package manager right now, i have  already ia32-libs installed on my system.

thank you :)

---

### Post by giorgi81 on 2011-04-20
I have similar problem on my PC 32bit:
 
I downloadad from here [[COLOR=#005177]http://www.canon-europe.com/Support/Consumer_Products/products/printers/Laser/Laser_Shot_LBP2900.aspx?type=download&page=1[/COLOR]]("http://www.canon-europe.com/Support/Consumer_Products/products/printers/Laser/Laser_Shot_LBP2900.aspx?type=download&page=1") driver, installed it, but I cannot print anything [IMG]http://kubuntuforums.net/forums/Smileys/classic/sad.gif[/IMG] 
It recognizes the printer, asks to print test page, but when ordering to print nothing happens [IMG]http://kubuntuforums.net/forums/Smileys/classic/sad.gif[/IMG]
 
I looked to printer cd, but it contains only windows installers [IMG]http://kubuntuforums.net/forums/Smileys/classic/sad.gif[/IMG]
 
Ido not know what to do [IMG]http://kubuntuforums.net/forums/Smileys/classic/sad.gif[/IMG]

---

### Post by Rhohitman on 2011-07-24
Did Someone got it working.... :(

I have tried other printers but couldn't get my LPB2900 running ... something is really wrong. :(

---

