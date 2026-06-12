---
title: "Brother DCP-J125 64 bit printer driver  ------- SOLVED"
date: 2011-03-21
forum: Hardware
---

### Post by madallig on 2011-03-21
[SIZE=3]H[/SIZE][SIZE=3]i spent 4 hours trying to figure out how to get 32 bit driver to work correctly on 64 bit machine (Dell Vostro 3500) 

This is what worked for me:
The drivers will only install through terminal:

1. reinstall  ia32-libs - for 32 bit printer drivers to install on 64 bit machine

2. create this directory first  /var/spool/lpd/dcpj125

3. install this driver first:
sudo dpkg -i --force-architecture /home/asiasourcing/Downloads/dcpj125lpr-1.1.1-1.i386.deb

4. instsall this driver second:
sudo dpkg -i --force-architecture /home/asiasourcing/Downloads/dcpj125cupswrapper-1.1.1-1.i386.deb

There will be some error messages - just ignore them! ... the terminal will go slow for a while - that's OK!

Here is my complete terminal script that worked for me:

asiasourcing@asiasourcing-899070:~$ sudo dpkg -i --force-architecture /home/asiasourcing/Downloads/dcpj125lpr-1.1.1-1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package dcpj125lpr.
(Reading database ... 172291 files and directories currently installed.)
Unpacking dcpj125lpr (from .../dcpj125lpr-1.1.1-1.i386.deb) ...
Setting up dcpj125lpr (1.1.1-1) ...
mkdir: cannot create directory `/var/spool/lpd/dcpj125': No such file or directory
chown: cannot access `/var/spool/lpd/dcpj125': No such file or directory
chgrp: cannot access `/var/spool/lpd/dcpj125': No such file or directory
chmod: cannot access `/var/spool/lpd/dcpj125': No such file or directory
asiasourcing@asiasourcing-899070:~$ sudo dpkg -i --force-architecture /home/asiasourcing/Downloads/dcpj125lpr-1.1.1-1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 172309 files and directories currently installed.)
Preparing to replace dcpj125lpr 1.1.1-1 (using .../dcpj125lpr-1.1.1-1.i386.deb) ...
Unpacking replacement dcpj125lpr ...
Setting up dcpj125lpr (1.1.1-1) ...
asiasourcing@asiasourcing-899070:~$ sudo dpkg -i --force-architecture /home/asiasourcing/Downloads/dcpj125cupswrapper-1.1.1-1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 172309 files and directories currently installed.)
Preparing to replace dcpj125cupswrapper 1.1.1-1 (using .../dcpj125cupswrapper-1.1.1-1.i386.deb) ...
Unpacking replacement dcpj125cupswrapper ...
Setting up dcpj125cupswrapper (1.1.1-1) ...
cups start/running, process 5435

asiasourcing@asiasourcing-899070:~$ 

[/SIZE]

---

### Post by alevian on 2011-07-30
Hi!

Here in Brazil my printer is working thanks to your hint.

---

### Post by rahuman on 2013-01-17
Hi madallig,

This helped me out alot. Thanks.BTW, The new version of drivers I got from the brother site didn't give any error. Thanks.

---

### Post by denixsi on 2013-03-07
I'm also from Brazil and your hint worked very well for me, an additional information is, if your printer is in your network lan, just right click in the printer properties and change device URI for your printer network location. Thanks madallig!


I'm using Ubuntu 12.04 (precise) 64-bit

---

