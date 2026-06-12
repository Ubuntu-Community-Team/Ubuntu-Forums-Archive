---
title: "[SOLVED] Mythbuntu?"
date: 2008-11-11
forum: General Help
---

### Post by Yezinki on 2008-11-11
Hi there,

I want to install Mythbuntu on Ubuntu 8.10 .....what do I do?

Regards,

Yezinki.

---

### Post by fenian on 2008-11-11
Install mythbuntu control centre from synaptic or with the command...
> 
sudo apt-get install mythbuntu-control-centre

Then start mythbuntu-control-centre from the menu System>Administration>Mythbuntu Control Centre.
In the control centre window click the system roles button.
Check both Primary Backend and Frontend and click the apply button.
It will install the Mythtv packages.
After it installs the packages refer to the [Mythbuntu documentation]("http://www.mythbuntu.org/installation_manual") for further info on completing setup.

---

### Post by Yezinki on 2008-11-11
Thanks.......

Would I be able to watch cable TV using it?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-11
ubuntu@ubuntu-laptop:~$ sudo apt-get install mythbuntu-control-centre 
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-xext-dev x11proto-kb-dev libxi-dev
  libxdmcp-dev libsnack2 xtrans-dev x11proto-core-dev amsn-data libxt-dev
  libxext-dev x11proto-input-dev libpthread-stubs0-dev libxau-dev
  libpthread-stubs0 tcl8.5 tk8.4 tk8.5 libx11-dev libxcb-xlib0-dev libxcb1-dev
  tcl-tls
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dialog expect libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  lirc mysql-client mysql-client-5.0 mythbuntu-common mythbuntu-lirc-generator
  mythtv-common pwgen python-mysqldb setserial vnc4-common
Suggested packages:
  expectk dbishell lirc-modules-source lirc-x mysql-doc-5.0
  mythtv-backend-master mythtv-frontend displayconfig-gtk mythtv-doc
  mysql-server-5.0 mysql-server python-mysqldb-dbg vnc4server xvnc4viewer
  vncviewer
The following NEW packages will be installed:
  dialog expect libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  lirc mysql-client mysql-client-5.0 mythbuntu-common mythbuntu-control-centre
  mythbuntu-lirc-generator mythtv-common pwgen python-mysqldb setserial
  vnc4-common
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.0MB of archives.
After this operation, 36.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/universe dialog 1.1-20080316-1 [264kB]
Get:2 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main setserial 2.17-44.2 [51.1kB]
Get:3 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/universe lirc 0.8.3-0ubuntu2 [402kB]
Get:4 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main expect 5.43.0-16 [317kB]      
Get:5 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main libnet-daemon-perl 0.38-1.1 [45.9kB]
Get:6 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main libplrpc-perl 0.2017-1.1 [35.0kB]
Get:7 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main libdbi-perl 1.605-1 [787kB]   
Get:8 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main libdbd-mysql-perl 4.007-1build1 [140kB]
Get:9 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main mysql-client-5.0 5.0.67-0ubuntu6 [7879kB]
Get:10 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main mysql-client 5.0.67-0ubuntu6 [52.7kB]                                                                                                                       
Get:11 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/universe mythbuntu-lirc-generator 0.20-0ubuntu1 [12.2kB]                                                                                                         
Get:12 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/universe mythbuntu-common 0.19-0ubuntu1 [19.1kB]                                                                                                                 
Get:13 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main python-mysqldb 1.2.2-7 [95.9kB]                                                                                                                             
Get:14 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/universe vnc4-common 4.1.1+xorg1.0.2-0ubuntu7 [17.2kB]                                                                                                           
Get:15 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main pwgen 2.06-1 [19.5kB]                                                                                                                                       
Get:16 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/multiverse mythtv-common 0.21.0+fixes18722-0ubuntu1 [5703kB]                                                                                                     
Get:17 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/universe mythbuntu-control-centre 0.31-0ubuntu1 [111kB]                                                                                                          
Fetched 16.0MB in 4min49s (55.0kB/s)                                                                                                                                                                          
Preconfiguring packages ...
Selecting previously deselected package dialog.
(Reading database ... 129772 files and directories currently installed.)
Unpacking dialog (from .../dialog_1.1-20080316-1_i386.deb) ...
Selecting previously deselected package setserial.
Unpacking setserial (from .../setserial_2.17-44.2_i386.deb) ...
Processing triggers for man-db ...
Setting up dialog (1.1-20080316-1) ...
Selecting previously deselected package lirc.
(Reading database ... 129919 files and directories currently installed.)
Unpacking lirc (from .../lirc_0.8.3-0ubuntu2_i386.deb) ...
Selecting previously deselected package expect.
Unpacking expect (from .../expect_5.43.0-16_i386.deb) ...
Selecting previously deselected package libnet-daemon-perl.
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1.1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1.1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.605-1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.007-1build1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.67-0ubuntu6_i386.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.0.67-0ubuntu6_all.deb) ...
Selecting previously deselected package mythbuntu-lirc-generator.
Unpacking mythbuntu-lirc-generator (from .../mythbuntu-lirc-generator_0.20-0ubuntu1_all.deb) ...
Selecting previously deselected package mythbuntu-common.
Unpacking mythbuntu-common (from .../mythbuntu-common_0.19-0ubuntu1_all.deb) ...
Selecting previously deselected package python-mysqldb.
Unpacking python-mysqldb (from .../python-mysqldb_1.2.2-7_i386.deb) ...
Selecting previously deselected package vnc4-common.
Unpacking vnc4-common (from .../vnc4-common_4.1.1+xorg1.0.2-0ubuntu7_i386.deb) ...
Selecting previously deselected package pwgen.
Unpacking pwgen (from .../archives/pwgen_2.06-1_i386.deb) ...
Selecting previously deselected package mythtv-common.
Unpacking mythtv-common (from .../mythtv-common_0.21.0+fixes18722-0ubuntu1_all.deb) ...
Selecting previously deselected package mythbuntu-control-centre.
Unpacking mythbuntu-control-centre (from .../mythbuntu-control-centre_0.31-0ubuntu1_all.deb) ...
Adding `diversion of /usr/share/mythtv/main_settings.xml to /usr/share/mythtv/main_settings.xml.diverted by mythbuntu-control-centre'
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                                                                                                                                                           [ OK ] 
Setting up setserial (2.17-44.2) ...
removing the old setserial entry in the rcn.d directories
Update complete.
Saving state of known serial devices... backing up /var/lib/setserial/autoserial.conf done.

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************


Setting up lirc (0.8.3-0ubuntu2) ...
 * Reloading kernel event manager...                                                                                                                                                                    [ OK ] 
 * Loading LIRC modules                                                                                                                                                                                 [ OK ] 
 * Starting remote control daemon(s) : LIRC                                                                                                                                                             [ OK ] 

Setting up expect (5.43.0-16) ...

Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.605-1) ...
Setting up libdbd-mysql-perl (4.007-1build1) ...
Setting up mysql-client-5.0 (5.0.67-0ubuntu6) ...
Setting up mysql-client (5.0.67-0ubuntu6) ...
Setting up mythbuntu-lirc-generator (0.20-0ubuntu1) ...

Setting up mythbuntu-common (0.19-0ubuntu1) ...

Setting up python-mysqldb (1.2.2-7) ...

Setting up vnc4-common (4.1.1+xorg1.0.2-0ubuntu7) ...

Setting up pwgen (2.06-1) ...
Setting up mythtv-common (0.21.0+fixes18722-0ubuntu1) ...
Adding user mythtv to group video
Adding user mythtv to group audio
Adding user mythtv to group cdrom
Adding user mythtv to group dialout

Setting up mythbuntu-control-centre (0.31-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-11-11
1. I have a Sony XP Media Center, USB infra red Transceiver.

2. TV Tuner is NTSC Fujitsu

3. Where is the password stored?

Regards,

Yezinki.

---

### Post by fenian on 2008-11-11
For the remote choose Windos Media Center (New Versio Phillips et. al)

As for the tuner I don't know if that tuner is supported in linux or not.You can check at [linuxtv.org]("http://www.linuxtv.org/")

The password is stored in /etc/mythtv/mysql.txt

---

### Post by Yezinki on 2008-11-11
Thanks.....whats the command for Terminal to check hard ware info?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-11
Your views about the screen shot?

---

### Post by fenian on 2008-11-11
To check hardware run...

dmesg

you should see your tuner card listed somewhere if it is detected.

---

