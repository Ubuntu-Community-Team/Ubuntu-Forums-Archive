---
title: "Newbie to ubuntu need help installing Brother MFCJ4620DW drivers"
date: 2018-04-02
forum: Hardware
---

### Post by kashi2018 on 2018-04-02
Good day everyone. 

I am newbie to Linux-ubuntu world coming from windows. I had windows 8.1 on my ASUS K56CA 64BIT Machine. My hard drive went bad. I installed new hard drive but no windows OS to reinstall. So I decided to Ditch Windows and trying Linux first time. So far so good. 

I was able to install Brother MFC-J4620DW printer drive successfully.

I am unable to install Scanner driver. 

[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj4620dw_us_eu_as&os=127](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj4620dw_us_eu_as&os=127)


[LIST]
[*]Download the driver.
[*]Login as a superuser.
[*]Install the driver.
[LIST]
[*]Turn on your MFC/DCP and connect the USB cable.
[*]Open the terminal and go to the directory where the driver is.
[*]Install the scanner driver.
**Command (for rpm) : rpm  -ihv  --nodeps  (scanner-drivername)**
[/LIST]
[/LIST]
OEM@MyDesktop:~/Downloads$ sudo rpm  -ihv  --nodeps brscan4-0.4.4-4.x86_64.rpm  [INDENT][sudo] password for oem: [/INDENT]
[INDENT]rpm: RPM should not be used directly install RPM packages, use Alien instead![/INDENT]
[INDENT]rpm: However assuming you know what you are doing...[/INDENT]
[INDENT]Preparing...                          ################################# [100%][/INDENT]
[INDENT]Updating / installing...[/INDENT]
[INDENT]   1:brscan4-0.4.4-4                  ################################# [100%][/INDENT]
[INDENT]This software is based in part on the work of the Independent JPEG Group.[/INDENT]
[INDENT]OEM@MyDesktop:~/Downloads$[/INDENT]


Scanner did not install?

kindly help me get this scanner installed.

---

### Post by wildmanne39 on 2018-04-02
*Thread moved to **Hardware, a more appropriate forum**.*

---

### Post by gifford on 2018-04-03
Please provide the version of Ubuntu you are using to allow others to help you. Just from what you provided, Ubuntu uses deb files, not RPM which is for Red Hat and other derivatives. It seems you have downloaded 
and tried to install the wrong package for your system.

---

### Post by kashi2018 on 2018-04-03
Thank you gifford for reply. I am using ubuntu 16.04. Only RPM scanner drivers available.
 
@[[COLOR=#C61919]wildmanne39[/COLOR]]("https://ubuntuforums.org/member.php?u=508533")[COLOR=#000000] How do I locate my Post in [/COLOR]
[h=1]Forum: Hardware?[/h][COLOR=#000000]Hardware? [/COLOR]

---

### Post by wildmanne39 on 2018-04-03
You already have, this is the post. When we move a post there is a redirect left in the sub-forum that you placed your thread in and you click on it and you are taken to your thread.

---

### Post by kashi2018 on 2018-04-03
@gifford I found the deb file and followed the brother website instructions.

[COLOR=#000000]OEM@MyDesktop[/COLOR]:~/Downloads$ ls
brscan4-0.4.4-4.i386.deb           uninstaller_brscan4
uninstaller_brscan-skey
linux-brprinter-installer-2.2.0-1  uninstaller_MFCJ4620DW


[COLOR=#000000]OEM@MyDesktop[/COLOR]:~/Downloads$ dpkg -i --force-all  brscan4-0.4.4-4.i386.deb
dpkg: error: operation requires read/write access to dpkg status area
[COLOR=#000000]OEM@MyDesktop[/COLOR]:~/Downloads$ sudo dpkg -i --force-all  brscan4-0.4.4-4.i386.deb
[sudo] password for oem: 
(Reading database ... 300884 files and directories currently installed.)
Preparing to unpack brscan4-0.4.4-4.i386.deb ...
Unpacking brscan4:i386 (0.4.4-4) over (0.4.4-4) ...
Setting up brscan4:i386 (0.4.4-4) ...
This software is based in part on the work of the Independent JPEG Group.
[COLOR=#000000]OEM@MyDesktop[/COLOR]:~/Downloads$ ls 
brscan4-0.4.4-4.i386.deb           uninstaller_brscan4
uninstaller_brscan-skey
linux-brprinter-installer-2.2.0-1  uninstaller_MFCJ4620DW
[COLOR=#000000]OEM@MyDesktop[/COLOR]:~/Downloads$ dpkg -l | grep mfcj4620dw
ii  mfcj4620dwcupswrapper:i386                  3.0.1-1                                                  i386         Brother CUPS Inkjet Printer Definitions
ii  mfcj4620dwlpr:i386                          3.0.1-1                                                  i386         Brother lpr Inkjet Printer Definitions
[COLOR=#000000]OEM@MyDesktop[/COLOR]:~/Downloads$ 


I search for Scanner in Application but only Simple Scanner App is available.Clicking this app says no scanner available.

Kindly help.

---

### Post by kashi2018 on 2018-04-03
I reinstall the Printer Driver and used USB wire for Scanner this time instead of network scan. Scanner Working with USB. I can scan documents from Flatbed and ADF with Simple Scan. I am unable to do network  Scan from the Touch screen on Printer.

---

### Post by kurt18947 on 2018-04-03
> **kashi2018 said:**
> I reinstall the Printer Driver and used USB wire for Scanner this time instead of network scan. Scanner Working with USB. I can scan documents from Flatbed and ADF with Simple Scan. I am unable to do network  Scan from the Touch screen on Printer.

The network scanner requires a one line command to get the scanner and Ubuntu recognize one another. I'll see if I can find it and post back. The bad news that as far as I can tell, neither Ubuntu 18.04 - or 17.10 recognize the Brother scanner using current Brother drivers. I have a Samsung MFD which works perfectly in 16.04 but not in 17.10 or 18.04 which makes me wonder if there's something that needs tweaks with SANE or something.

Edit: Here are the directions for installing Brother scanners. Have you completed step 5? One nice thing about the network install is that you don't have to worry about editing the udev libsane rule.

[http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on)

I haven't had to do step 2 in those directions for at least 5 years I'd guess.

---

### Post by kashi2018 on 2018-04-04
Thanks for your help. 

I have gone through all the steps.


[LIST]
[*]Download the driver.
[*] brscan4-0.4.4-4.i386.deb
[*]Login as a superuser (or use "sudo" option if required) .
[*]Check if pre-required procedures are completed 
[**For Debian, Ubuntu**]("http://support.brother.com/g/s/id/linux/en/before.html#101")
[*]Install the driver.
[LIST]
[*]Turn on your MFC/DCP and connect the USB cable.
[*]Open the terminal and go to the directory where the driver is.
[*]Install the scanner driver.
**Command (for dpkg) : dpkg -i --force-all  (scanner-drivername)**
[/LIST]

[*]oem@MYPC:~/Downloads$ sudo dpkg -i --force-all brscan4-0.4.4-4.i386.deb[sudo] password for oem: 
(Reading database ... 305360 files and directories currently installed.)
Preparing to unpack brscan4-0.4.4-4.i386.deb ...
Unpacking brscan4:i386 (0.4.4-4) over (0.4.4-3) ...
Setting up brscan4:i386 (0.4.4-4) ...
This software is based in part on the work of the Independent JPEG Group.
[*]
[LIST]
[*]Check if the driver is installed.
**Command (for dpkg) : dpkg -l | grep Brother**
 This command did not work . I do not have PIPE symbol on the Keyboard. So i ran it without it.
[*]oem@MYPC:~/Downloads$ sudo dpkg -i grep Brother
dpkg: error processing archive grep (--install):
 cannot access archive: No such file or directory
dpkg: error processing archive Brother (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 grep
 Brother
oem@MYPC:~/Downloads$
[/LIST]

[*]
**For USB Users:**[INDENT]Use your scanning application by a superuser and try a test scan.
[**Use your usb-connectrd scanner by a normal user**]("http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html")[/INDENT]
**For Network Users:**[INDENT][HR][/HR]***Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2 models), brsaneconfig3 (for brscan3 models) or brsaneconfig4 (for brscan4 models) accordingly.[HR][/HR]
Add network scanner entry
[B]Command : Brsaneconfig4 -a name=(name your device) model=(model name) ip=xx.xx.xx.xx
[/B]
---------------------** Brsaneconfig4 command not found**

Confirm network scanner entry
**Command : brsaneconfig4 -q | grep (name of your device)**

Open a scanner application and try a test scan.


- SCAN to FILE ICON on Printer Display Bring the USER OEM but not working timing out....


- It maybe firewall issue. I have no idea how to open ports in Firewall, all i can do is add ports in firewall.

[/INDENT]
[/LIST]
**How to Install**

[COLOR=#000000][FONT=sans-serif]
[LIST]
[*]Download LPR driver.
[*]Login as a superuser (or use "sudo" option if required).
[*]Check if pre-required procedures are completed
[For Ubuntu]("http://support.brother.com/g/s/id/linux/en/before.html#101")
[For Distributions using firewall]("http://support.brother.com/g/s/id/linux/en/before.html#103")
GIMP is required for "scan-to-image"
brscanX should be installed first
[*]Install the driver.
[LIST]
[*]Open the terminal and go to the directory where the driver is.
[*]Install the scan-key-tool.
**Command  :  dpkg -i  --force-all  (scan-key-tool filename)**
[/LIST]

[*]oem@MYPC:~/Downloads$ sudo dpkg -i  --force-all brscan-skey-0.2.4-1.i386.deb[sudo] password for oem: 
(Reading database ... 305360 files and directories currently installed.)
Preparing to unpack brscan-skey-0.2.4-1.i386.deb ...
Unpacking brscan-skey:i386 (0.2.4-1) over (0.2.4-1) ...
Setting up brscan-skey:i386 (0.2.4-1) ...
oem@MYPC:~/Downloads$
[LIST]
[*]Check if the scanner driver is installed.
**Command  :  dpkg -l  |  grep  Brother ------------- Not working**
[/LIST]

[*]Run scan-key-tool and try the test scanning.
[LIST]
[*]Run scan-key-tool(The program will run as a background process.)  
**Command  :  brscan-skey - worked no error**
[*]Check if the scan-key-tool detect your scanner device.
**Command  :  brscan-skey -l worked no error**
[*]Press the scan button, select user, select destination, press START.
[/LIST]
[/LIST]
Simple Scan Application can't find the Scanner when computer is not connected with printer with USB

[/FONT][/COLOR]

---

### Post by kashi2018 on 2018-04-04
Here is my complete Install.

oem@SYSBUILDOEM2018:~$ cd ~/Downloads && gunzip -v ~/Downloads/linux-brprinter*
/home/oem/Downloads/linux-brprinter-installer-2.2.0-1.gz:	 82.8% -- replaced with /home/oem/Downloads/linux-brprinter-installer-2.2.0-1
oem@SYSBUILDOEM2018:~/Downloads$ sudo bash ~/Downloads/linux-brprinter*
[sudo] password for oem: 
Input model name ->mfcj4620dw


You are going to install following packages.
   mfcj4620dwlpr-3.0.1-1.i386.deb
   mfcj4620dwcupswrapper-3.0.1-1.i386.deb
   brscan4-0.4.4-3.amd64.deb
   brscan-skey-0.2.4-1.amd64.deb
OK? [y/N] ->y




=========================================
Brother License Agreement


Brother retains any and all copyrights to the Software. In no case this Agreement shall be construed to assign or otherwise transfer from Brother to User any copyrights or other intellectual property rights to whole or any part of the Software.


Brother grants User a non-exclusive license: to reproduce and/or distribute (via Internet or in any other manner) the Software. Further, Brother grants User a non-exclusive license to modify, alter, translate or otherwise prepare derivative works of the Software and to reproduce and distribute (via Internet or in any other manner) such modification, alteration, translation or other derivative works for any purpose.


The license of the Software from Brother hereunder is granted "AS IS." BROTHER HEREBY DISCLAIMS ANY WARRANTIES WITH RESPECT TO THE SOFTWARE, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO WARRANTY FOR THE QUALITY, MERCHANTABILITY, FITNESS FOR PARTICULAR PURPOSE OR NON-INFRINGEMENT.
Brother shall have no liability in contract, tort (including negligence or breach of statutory duty) or otherwise for any interruption of use, loss of data, or for any indirect, incidental, punitive or consequential loss or damage, or for any loss of profit, revenue, data, goodwill or anticipated savings that arises under, out of, or in contemplation of this Agreement or otherwise arises due to any error, inaccuracy or defect in the Software even if Brother has been advised of the possibility of such loss or damage.
Further, Brother shall have no liability to disclose and/or distribute the source cord of the Software to User under any circumstances. In no case shall the above license by Brother to modify, alter, translate or otherwise prepare derivative works of the Software be construed as Brother's implied agreement or undertakings to disclose and/or distribute the source cord of the Software.
=========================================
Do you agree? [Y/n] ->y


wget -T 10 -nd --no-cache [http://www.brother.com/pub/bsc/linux/packages/mfcj4620dwlpr-3.0.1-1.i386.deb](http://www.brother.com/pub/bsc/linux/packages/mfcj4620dwlpr-3.0.1-1.i386.deb)
--2018-04-04 09:52:34--  [http://www.brother.com/pub/bsc/linux/packages/mfcj4620dwlpr-3.0.1-1.i386.deb](http://www.brother.com/pub/bsc/linux/packages/mfcj4620dwlpr-3.0.1-1.i386.deb)
Resolving [www.brother.com](www.brother.com) ([www.brother.com](www.brother.com))... 23.205.120.17, 23.205.120.67
Connecting to [www.brother.com](www.brother.com) ([www.brother.com)|23.205.120.17|:80](www.brother.com)|23.205.120.17|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2803864 (2.7M) [text/plain]
Saving to: &#8216;mfcj4620dwlpr-3.0.1-1.i386.deb&#8217;


mfcj4620dwlpr-3.0.1 100%[===================>]   2.67M  --.-KB/s    in 0.1s    


2018-04-04 09:52:34 (17.8 MB/s) - &#8216;mfcj4620dwlpr-3.0.1-1.i386.deb&#8217; saved [2803864/2803864]


Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Hit:7 [http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu) xenial InRelease     
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-proposed InRelease [253 kB]
Fetched 560 kB in 0s (664 kB/s)                              
Reading package lists... Done
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
dpkg -x mfcj4620dwlpr-3.0.1-1.i386.deb /
dpkg -x mfcj4620dwcupswrapper-3.0.1-1.i386.deb /
dpkg-deb: building package 'mfcj4620dwlpr' in 'mfcj4620dwlpr-3.0.1-1a.i386.deb'.
dpkg -b ./brother_driver_packdir mfcj4620dwlpr-3.0.1-1a.i386.deb
dpkg-deb: building package 'mfcj4620dwcupswrapper' in 'mfcj4620dwcupswrapper-3.0.1-1a.i386.deb'.
dpkg -b ./brother_driver_packdir mfcj4620dwcupswrapper-3.0.1-1a.i386.deb
dpkg -i --force-all mfcj4620dwlpr-3.0.1-1a.i386.deb
(Reading database ... 305356 files and directories currently installed.)
Preparing to unpack mfcj4620dwlpr-3.0.1-1a.i386.deb ...
Unpacking mfcj4620dwlpr:i386 (3.0.1-1) over (3.0.1-1) ...
Setting up mfcj4620dwlpr:i386 (3.0.1-1) ...
mkdir: cannot create directory &#8216;/var/spool/lpd/mfcj4620dw&#8217;: No such file or directory
chown: cannot access '/var/spool/lpd/mfcj4620dw': No such file or directory
chgrp: cannot access '/var/spool/lpd/mfcj4620dw': No such file or directory
chmod: cannot access '/var/spool/lpd/mfcj4620dw': No such file or directory
dpkg -i --force-all mfcj4620dwcupswrapper-3.0.1-1a.i386.deb
Selecting previously unselected package mfcj4620dwcupswrapper:i386.
(Reading database ... 305356 files and directories currently installed.)
Preparing to unpack mfcj4620dwcupswrapper-3.0.1-1a.i386.deb ...
Unpacking mfcj4620dwcupswrapper:i386 (3.0.1-1) ...
Setting up mfcj4620dwcupswrapper:i386 (3.0.1-1) ...
Restarting cups (via systemctl): cups.service.
lpadmin -p MFCJ4620DW -E -v usb://Brother/MFC-J4620DW?serial=BROM5F204097 -P /usr/share/cups/model/Brother/brother_mfcj4620dw_printer_en.ppd
#
Will you specify the Device URI? [Y/n] ->y




0: socket
1: https
2: ipps
3: ipp
4: lpd
5: beh
6: ipp14
7: http
8: usb://Brother/MFC-J4620DW?serial=BROM5F204097
9: hp
10: hpfax
11: dnssd://Brother%20MFC-J4620DW._ipp._tcp.local/?uuid=e3248000-80ce-11db-8000-30055cad20d2
12 (I): Specify IP address.
13 (A): Auto. (usb://Brother/MFC-J4620DW?serial=BROM5F204097)


select the number of destination Device URI. ->12


 enter IP address ->192.168.0.201
lpadmin -p MFCJ4620DW -v socket://192.168.0.201 -E
Test Print? [y/N] ->y


wait 5s.
lpr -P MFCJ4620DW /usr/share/cups/data/testprint
You are going to install following packages.
   brscan4-0.4.4-3.amd64.deb
dpkg -i --force-all brscan4-0.4.4-3.amd64.deb
(Reading database ... 305360 files and directories currently installed.)
Preparing to unpack brscan4-0.4.4-3.amd64.deb ...
Unpacking brscan4 (0.4.4-3) over (0.4.4-3) ...
Setting up brscan4 (0.4.4-3) ...
This software is based in part on the work of the Independent JPEG Group.
You are going to install following packages.
   brscan-skey-0.2.4-1.amd64.deb
dpkg -i --force-all brscan-skey-0.2.4-1.amd64.deb
(Reading database ... 305360 files and directories currently installed.)
Preparing to unpack brscan-skey-0.2.4-1.amd64.deb ...
Unpacking brscan-skey (0.2.4-1) over (0.2.4-1) ...
Setting up brscan-skey (0.2.4-1) ...
brsaneconfig4 -a name=MFC-J4620DW model=MFC-J4620DW ip=192.168.0.201
Hit Enter/Return key.

---

### Post by kashi2018 on 2018-04-04
Network Scan is working one way. From computer using Simple Scan I can scan documents wireless but I can not scan documents and send File to computer from the Touch Screen on Scanner.

---

### Post by kurt18947 on 2018-04-04
> **kashi2018 said:**
> Network Scan is working one way. From computer using Simple Scan I can scan documents wireless but I can not scan documents and send File to computer from the Touch Screen on Scanner.

It sounds like you have network scanning working, good job. I'm not much help with brscan-key-tool, never had a use where it made sense. I use gscan2pdf for arranging and editing scans which works well for my needs.

---

### Post by gifford on 2018-04-04
I would recommend using the xsane imaging scanning program. You will place the items to be scanned in your scanner and then scan them from your computer. I have used this application
for years with Brother printer/scanners and have never had any problems.

---

