---
title: "Motorola SM56 PCI (11d4:1805), Ubuntu 7.04, Kernel 2.6.20-15-generic"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by lightning18 on 2007-08-01
[COLOR=black]I have a Motorola SM56 Data/Fax/Speakerphone (11d4:1805) Modem and I would like to install it on Ubuntu Linux 7.04 Feisty Fawn.[/COLOR]
[COLOR=black]I am a Linux Noob and not a modem expert.[/COLOR]
[COLOR=black]I need the help of the Linux Experts (Ubuntu) and Modem Experts out there!!![/COLOR]
[COLOR=black]I believe that the driver I need to use is the sl modem.[/COLOR]
[COLOR=black]I have a newly installed Ubuntu 7.04 dual-booted with WinXPPro with the modem installed. I use XP to download the packages that I believe that I need to install the modem on Ubuntu. I have tried to follow some of the instruction on the net but I didn't find any successful.
Some have the real SM56 Driver but for other Linux Distro.[/COLOR]
 
[COLOR=black]I used the pre-compiled drivers, slamr-2.6.20-15-generic.tar.gz. I "sudo ./setup" on the terminal and this is what i got:[/COLOR]
 
[COLOR=black]> [/COLOR]
[SIZE=2][COLOR=black]lightning18@abiera-desktop:~/Desktop/slmodem$ sudo ./setup [/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]driver=slamr[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]When asked about your country, Enter:[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]        USA[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Installing the Debian packages supporting autoloading[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black](Reading database ... 90439 files and directories currently installed.)[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Preparing to replace sl-modem-daemon 2.9.10+2.9.9d+e-pre2-5build1 (using sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb) ...[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Shutting down SmartLink Modem driver normally ... no slmodemd daemon running.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Unloading modem driver from kernel ... slamr.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Unpacking replacement sl-modem-daemon ...[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Setting up sl-modem-daemon (2.9.10+2.9.9d+e-pre2-5build1) ...[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Starting SmartLink Modem driver for: slamr0.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Creating /dev/modem symlink, pointing to: /dev/ttySL0.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][/SIZE][SIZE=2][COLOR=black]Copying over newer files[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]cp: cannot stat `sl-modem-daemon.modutils': No such file or directory[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Making folder /lib/modules/2.6.20-15-generic/extra[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Copying drivers to /lib/modules/2.6.20-15-generic/extra[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Checking driver install[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]slamr.ko  slusb.ko  ungrab-winmodem.ko[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Finished installs.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Informing the System[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Starting function tests, loading drivers:[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Running diagnostic:[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black][   48.098682] slamr: module license 'Smart Link Ltd.' taints kernel.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black][   48.107748] slamr: SmartLink AMRMO modem.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black][   48.107894] slamr: probe 11d4:1805 SL1900 card...[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black][   48.108008] slamr: cannot init card.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black][  177.920715] slamr: SmartLink AMRMO modem.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black][  177.924842] slamr: probe 11d4:1805 SL1900 card...[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black][  177.925668] slamr: cannot init card.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black][  239.642059] slamr: SmartLink AMRMO modem.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black][  239.646275] slamr: probe 11d4:1805 SL1900 card...[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black][  239.647082] slamr: cannot init card.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]ports should be created by:[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]slmodemd -c USA /dev/slamr0[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]error: mdm setup: cannot open dev `/dev/slamr0': No such device[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]error: cannot setup device `/dev/slamr0'[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Checking for success[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Port creation with slmodemd failed.[/COLOR][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][COLOR=black]Read the Slamr.txt record, other 1st_Read.txt CountryList.txt Unload.txt wvdial.txt files and the sample wvdial.conf.[/COLOR][/SIZE][SIZE=2][/SIZE]

[COLOR=black][/COLOR]
 

[COLOR=#000000]I think the problem is the "[SIZE=2][COLOR=black]cp: cannot stat `sl-modem-daemon.modutils': No such file or directory" and the "slamr: cannot init card."[/COLOR][/SIZE][/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000][SIZE=2]Could someone help me with this problem?[/SIZE][/COLOR]
[COLOR=#000000]or[/COLOR]
[COLOR=#000000]Could someone tell me how to use/install/configure this SM56 Modem on Ubuntu 7.04 (not any other linux distro) to get it working?[/COLOR]
 
[COLOR=#000000]Attached herewith is the result of the scanModem.[/COLOR]
[COLOR=#000000]> [/COLOR]
[COLOR=#000000][SIZE=2]-------------------------- System information ----------------------------
CPU=i686, Ubuntu 7.04 
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
scanModem update of: 2007_July_16
The modem symbolic link is /dev/modem -> ttySL0
ALSAversion 1.0.13
USB modem not detected by lsusb
Modem or host audio card candidates have firmware information:
PCI slot PCI ID SubsystemID Name
---------- --------- --------- --------------
00:10.0 11d4:1805 11d4:1805 Communication controller: Analog Devices SM56 PCI modem
Modem interrupt assignment and sharing: 
--- Bootup diagnostics for card in PCI slot 00:10.0 ----
[ 68.080147] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 19 (level, low) -> IRQ 17
[ 68.080251] ACPI: PCI interrupt for device 0000:00:10.0 disabled
The PCI slot 00:10.0 of the modem card may be disabled early in 
a bootup process, but then enabled later. If modem drivers load 
but the modem is not responsive, read Bootup.txt about possible fixes.
Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
if help is needed.

=== Finished modem firmware and bootup diagnostics section. ===
=== Next deducing cogent software ===
For candidate modem in PCI bus: 00:10.0
Class 0780: 11d4:1805 Communication controller: Analog Devices SM56 PCI modem
Primary PCI_id 11d4:1805
Support type needed or chipset: Motorola

 
Completed candidate modem analyses.
The base of the UDEV device file system is: /dev/.udev
Versions adequately match for the compiler installed: 4.1.2
and the compiler used in kernel assembly: 4.1.2
Kernel-header resources needed for compiling are not manifestly ready!
If compiling is necessary packages must be installed, providing:
linux-headers-2.6.20-15-generic
Compressed files at: /usr/src/--sl-modem.tar.bz2
 
Checking pppd properties:
-rwsr-xr-x 1 root dip 269224 2007-04-05 11:41 /usr/sbin/pppd
In case of an "error 17" "serial loopback" problem, see:
[http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)
To enable dialout without Root permission do:
$ su - root (not for Ubuntu)
sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
sudo chmod a+x /usr/sbin/pppd
Checking settings of: /etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx
In case of a message like:
Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)
 
Don't worry about the following, it is for the experts
should trouble shooting be necessary.
==========================================================
# start/stop the daemon when the USB modem is connected
KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
Checking for modem support lines:
--------------------------------------
/device/modem symbolic link: lrwxrwxrwx 1 root root 6 2007-07-31 19:34 /dev/modem -> ttySL0
slmodemd created symbolic link /dev/ttySL0: 
Within /etc/udev/ files:
/etc/udev/sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/sl-modem-daemon.modutils:install slamr modprobe --ignore-install ungrab-winmodem ; modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0) 
Within any ancient /etc/devfs files:
Within ancient kernel 2.4.n /etc/module.conf files:
/etc/modules~:ungrab-winmodem
--------- end modem support lines --------
[/SIZE][/COLOR][COLOR=#000000][/COLOR]
 
[COLOR=#000000]I NEED HELP![/COLOR]

---

### Post by helmut_hed on 2007-08-06
Unfortunately this modem is not supported under Linux.  I've tried it myself... the Smartlink driver looks like it will work, but does not.  11d4:1805 is a Motorola modem that does not work.  1057:3052 is a Motorola modem that DOES work.  I guess they are different.  Anyway that's my experience.

Regards,
Jeff

---

