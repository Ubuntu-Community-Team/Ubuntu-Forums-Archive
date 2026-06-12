---
title: "Trouble installing Brother printer"
date: 2011-10-13
forum: Hardware
---

### Post by tommy2k10 on 2011-10-13
I am running Ubuntu 64-bit.
I have a Brother DCP145C printer and am having trouble with the installation process.

Firstly, I installed the prerequisites:
**ia32-libs** or **lib32stdc++** is required to be installed.

Then I downloaded the rpm driver:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-145C](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-145C)

I got admin privileges by typing su root.

Then I typed:

# rpm -ihv --nodeps dcp145clpr-1.1.2-2.i386.rpm[FONT=Verdana]after which I got told I needed to install rpm's with Alien.  I looked this up, and typed:

[/FONT]sudo apt-get install alien dpkg-dev debhelper build-essential

[FONT=Verdana]then:

[/FONT]sudo alien dcp145clpr-1.1.2-2.i386rpm

[FONT=Verdana]then I followed the instructions on the Brother Linux driver installation web page, 
starting with the installation process:

[/FONT]# rpm -ihv --nodeps dcp145clpr-1.1.2-2.i386.rpm Preparing packages for installation... dcp145clpr-1.1.2-2 Shutting down cupsd                                                  done Starting cupsd                                                       done #
[FONT=Verdana](I didn't see the last two sentences)

then I checked to see if it was there, which it was:

[/FONT]# rpm -qa | grep -e dcp145clpr dcp145c-1.1.2-2.i386 #

[FONT=Verdana]then I tested the printcap USB connection[/FONT]:

$ cat /etc/printcap DCP145C:\         :mx=0:\         :sd=/var/spool/lpd/dcp145c:\         :sh:\         :lp=/dev/usb/lp0:\         :if=/usr/local/Brother/Printer/dcp145c/lpd/filterdcp145c: 
[FONT=Verdana]it is on lp0

then I restarted the print system:

[/FONT]/etc/init.d/lpr  restart
[FONT=Verdana](It said it didn't recognise this command)


Also, it kept telling me that i386 is the wrong architecture, which is right, but that 
shouldn't happen, as I installed the [/FONT]**ia32-libs** or **lib32stdc++ **packages.

What can I do now?

---

