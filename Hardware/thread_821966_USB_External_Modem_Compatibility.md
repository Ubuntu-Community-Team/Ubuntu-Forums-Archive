---
title: "USB External Modem Compatibility"
date: 2008-06-07
forum: Hardware
---

### Post by Pyro.699 on 2008-06-07
Hello,

I am currently a Dial-Up user who is running a 28.8kbs connection. I am looking to convert my windows XP computer (which is used to connect to dial-up via internal PCI Modem) to Ubuntu (i already have several Ubuntu computers). I know that most PCI modems don't work well and usually take a lot of time to set up and get working properly. I am going to buy an External modem and have 2 picked out  and wanted to know before i purchased them if they would work with Ubuntu 8.04.

[quote=Modem List]
[Hiro External USB 56K V.92 Modem](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=876411&sku=E261-1100)
[TRENDnet TFM-560U 56k (V.90) High Speed USB Fax Modem](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=671885&CatId=564)
[/quote]

Another question i have about this is if i get this done correctly and i get on the internet with one of these modems, is it possible for me to network the connection (As in share it between multiple computers). The computers it would be connecting to would be 2x Windows XP, 1x Windows Vista, 2x Ubuntu Hardy.

Thanks so much for any feedback.
~Cody Woolaver

---

### Post by Melvin1939 on 2011-01-23
> **Pyro.699 said:**
> Hello,

I am currently a Dial-Up user who is running a 28.8kbs connection. I am looking to convert my windows XP computer (which is used to connect to dial-up via internal PCI Modem) to Ubuntu (i already have several Ubuntu computers). I know that most PCI modems don't work well and usually take a lot of time to set up and get working properly. I am going to buy an External modem and have 2 picked out  and wanted to know before i purchased them if they would work with Ubuntu 8.04.



Another question i have about this is if i get this done correctly and i get on the internet with one of these modems, is it possible for me to network the connection (As in share it between multiple computers). The computers it would be connecting to would be 2x Windows XP, 1x Windows Vista, 2x Ubuntu Hardy.

Thanks so much for any feedback.
~Cody Woolaver

I have a TRENDnet TFM-560U Moden and I trying to get it to work, with Ubuntu 8.04.
I even tried to load under wine windows and with on luck.
I sure it can be done, but I do not know how yet.

---

### Post by fmdex2011 on 2011-03-05
I just installed a zoom 3095f usb modem on 2 laptops and a netbook

its more expensive than the trendnet but it installs quickly and works great on

ubuntu 10.10 i386 and amd64

---

### Post by ezeze5000 on 2011-08-21
I have a zoom 3095 56k usb modem, trying to install on a Toshiba Satellite A505D-S6958 Ubuntu 11.04.
I'm pretty rusty on the terminal command side of the house.
Could I get you to do a walk through on the install?

Here is what I have so far.
________________________________________________________________
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

jim@ubuntu:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates
jim@ubuntu:~$ cd Downloads
jim@ubuntu:~/Downloads$ ls
zoom3095
jim@ubuntu:~/Downloads$ cd zoom3095
jim@ubuntu:~/Downloads/zoom3095$ ls
3095_Linux-x86-106      3095_Win7-64bit_v20220.exe
3095_Linux-x86-106.zip  Zoom_3095F_Vista64.exe
jim@ubuntu:~/Downloads/zoom3095$ cd 3095_Linux-x86-106
jim@ubuntu:~/Downloads/zoom3095/3095_Linux-x86-106$ ls
debian                                                      ReadMe.pdf  tar
Distribution-specific binary packages (easiest to install)  rpm
jim@ubuntu:~/Downloads/zoom3095/3095_Linux-x86-106$ cd debian
jim@ubuntu:~/Downloads/zoom3095/3095_Linux-x86-106/debian$ ls
dgcmodem_1.06_i386.deb  LICENSE
jim@ubuntu:~/Downloads/zoom3095/3095_Linux-x86-106/debian$ sudo
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U user name] [-u
            user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] file ...
jim@ubuntu:~/Downloads/zoom3095/3095_Linux-x86-106/debian$ sudo bap2011tist
[sudo] password for jim: 
sudo: bap2011tist: command not found
jim@ubuntu:~/Downloads/zoom3095/3095_Linux-x86-106/debian$ sudo
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U user name] [-u
            user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] file ...
jim@ubuntu:~/Downloads/zoom3095/3095_Linux-x86-106/debian$ bap2011tist
bap2011tist: command not found
jim@ubuntu:~/Downloads/zoom3095/3095_Linux-x86-106/debian$ sudo dpkg -i dgcmodem_1.06_i386.deb
Selecting previously deselected package dgcmodem.
(Reading database ... 158210 files and directories currently installed.)
Unpacking dgcmodem (from dgcmodem_1.06_i386.deb) ...
Setting up dgcmodem (1.06) ...
Conexant DGC USB modem driver, version 1.06

If you need assistance or more information, please go to:
	[http://www.linuxant.com/](http://www.linuxant.com/)

When reporting a problem for the first time, please send
us the file generated by "dgcconfig --dumpdiag".

No pre-built modules for: Ubuntu-11.04 linux-2.6.38-11-generic i686-SMP:(

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

WARNING: missing file /lib/modules/2.6.38-11-generic/build/include/linux/autoconf.h
The cause of this is usually a missing or unconfigured
kernel source tree (and sometimes an incorrect directory or symbolic link).

However, proper /boot/config-2.6.38-11-generic was found.

Unable to prepare temporary kernel tree

First, ensure that the proper kernel source and compiler packages:(
from your distribution vendor and/or the community are installed.

The Linux kernel can then be reconfigured by running "make menuconfig"
under the kernel source directory (usually /usr/src/linux).

Verify that the proper options for your system are selected.

Then compile and install your new kernel (for more information about
this procedure, see the README file under the kernel source directory),
reboot the system using the new kernel, and re-run "dgcconfig".
jim@ubuntu:~/Downloads/zoom3095/3095_Linux-x86-106/debian$ dgcconfig
bash: /usr/sbin/dgcconfig: Permission denied
jim@ubuntu:~/Downloads/zoom3095/3095_Linux-x86-106/debian$ sudo dgcconfig
Conexant DGC USB modem driver, version 1.06

If you need assistance or more information, please go to:
	[http://www.linuxant.com/](http://www.linuxant.com/)

When reporting a problem for the first time, please send
us the file generated by "dgcconfig --dumpdiag".

No pre-built modules for: Ubuntu-11.04 linux-2.6.38-11-generic i686-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.38-11-generic/build] 

___________________________________________________

Any help would be appreciated.

Thanks

---

