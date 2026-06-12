---
title: "About Smartlink Modem installation in 8.10"
date: 2009-01-01
forum: Hardware
---

### Post by victan7300 on 2009-01-01
I am a user that have tried ubuntu and all sorts of Linux distros for a number of times that the modem is the problem that force me back to the "inferior" windows system that can decline in performance with time even I use it for e-mail receiving, fax and for playing Solitaire only (I use another Mac for daily work).

I found my modem is "ALi Corporation SmartLink SmartPCI563 56K Modem" from the scanModem result.

Please help me and I hope for your advice (but please don't give me answers like "go back to use Windows" the ITSC technicians have "answered" in my University). Thank you very much!

Besides, I use the modem only for fax receiving and sending, please also advice ways to make my computer for doing this, the best is that the fax function can act like printer service. Thank you very much once again!

That my problem is I cannot install the driver for my modem by following available "guides" found on Google: e.g. 

[https://help.ubuntu.com/community/DialupModemHowto/Smartlink](https://help.ubuntu.com/community/DialupModemHowto/Smartlink)
[http://ubuntuforums.org/showthread.php?t=190728](http://ubuntuforums.org/showthread.php?t=190728)

I have faced compile errors on compiling the codes:

1. make the "slmodem"

pobadmin@pobeditel:~/Desktop/slmodem-2.9.11-20080817$ make
make -C modem all
make[1]: Entering directory `/home/pobadmin/Desktop/slmodem-2.9.11-20080817/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_datafile.o -c modem_datafile.c
In function &#8216;open&#8217;,
    inlined from &#8216;datafile_save_info&#8217; at modem_datafile.c:114:
/usr/include/bits/fcntl2.h:51: error: call to &#8216;__open_missing_mode&#8217; declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[1]: *** [modem_datafile.o] Error 1
make[1]: Leaving directory `/home/pobadmin/Desktop/slmodem-2.9.11-20080817/modem'
make: *** [modem] Error 2
pobadmin@pobeditel:~/Desktop/slmodem-2.9.11-20080817$ 

2. sudo module-assistant auto-install sl-modem

dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean SUPPORT_ALSA=1
make[1]: Entering directory `/usr/src/modules/sl-modem'
make[1]: Leaving directory `/usr/src/modules/sl-modem'
cd modem; /usr/bin/make clean SUPPORT_ALSA=1
make[1]: Entering directory `/usr/src/modules/sl-modem/modem'
make[1]: Leaving directory `/usr/src/modules/sl-modem/modem'
dh_clean
/usr/bin/make -C drivers clean
make[1]: Entering directory `/usr/src/modules/sl-modem/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o&#9618;
amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~             
rm -f -r .tmp_versions
make[1]: Leaving directory `/usr/src/modules/sl-modem/drivers'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/sl-modem'
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean SUPPORT_ALSA=1
make[2]: Entering directory `/usr/src/modules/sl-modem'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/usr/src/modules/sl-modem'
make[1]: [clean] Error 2 (ignored)
cd modem; /usr/bin/make clean SUPPORT_ALSA=1
make[2]: Entering directory `/usr/src/modules/sl-modem/modem'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/usr/src/modules/sl-modem/modem'
make[1]: [clean] Error 2 (ignored)
dh_clean
/usr/bin/make -C drivers clean
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o
amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
rm -f -r .tmp_versions
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'
for templ in
/usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst
/usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.backup
/usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.module
s.in; do \
cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-7-generic/g'` ; \
done
for templ in `ls debian/*.modules.in` ; do \
test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in}
${templ%.modules.in}.backup 2>/dev/null || true; \ 
sed -e 's/##KVERS##/2.6.27-7-generic/g ;s/#KVERS#/2.6.27-7-generic/g
; s/_KVERS_/2.6.27-7-generic/g ; s/##KDREV##/2.6.27-7.14/g ;
s/#KDREV#/2.6.27-7.14/g ; s/_KDREV_/2.6.27-7.14/g  ' < $templ >
${templ%.modules.in}; \
done
dh_clean -k
dh_installdirs lib/modules/2.6.27-7-generic/misc usr/lib/sl-modem
if ! test -e drivers/Makefile ; then echo "Please update the package,
extract the tarball!"; exit 1 ; fi
/usr/bin/make -C drivers
KERNEL_DIR=/usr/src/linux-headers-2.6.27-7-generic KVERS=2.6.27-7-generic
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'
gcc -I/usr/src/linux-headers-2.6.27-7-generic/include -o kernel-ver
kernel-ver.c
kernel-ver.c: In function &#8216;main&#8217;:
kernel-ver.c:11: error: &#8216;UTS_RELEASE&#8217; undeclared (first use in this function)
kernel-ver.c:11: error: (Each undeclared identifier is reported only once
kernel-ver.c:11: error: for each function it appears in.)
make[2]: *** [kernel-ver] Error 1
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/module/sl-modem'
make: *** [kdist_build] Error 2                        
                


Records from ModemData.txt:

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.27-7-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008
 scanModem update of:  2008_12_27
The modem symbolic link is /dev/modem -> ttySL0
 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 1d6b:0002 Linux Foundation 2.0 root hub
 ID 06a2:0003 Topro Technology, Inc. 
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 1d6b:0002 Linux Foundation 2.0 root hub
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 093a:2500 Pixart Imaging, Inc. USB Optical Mouse
 ID 1d6b:0001 Linux Foundation 1.1 root hub

USB modems not recognized

For candidate card in slot 02:03.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 02:03.0	10b9:545a	201f:545a	Modem: ALi Corporation SmartLink SmartPCI563 56K Modem

 Modem interrupt assignment and sharing: 
  5:          2    XT-PIC-XT        ehci_hcd:usb7
 --- Bootup diagnostics for card in PCI slot 02:03.0 ----
[    0.713427] PCI: 0000:02:03.0 reg 10 32bit mmio: [eb001000, eb001fff]
[    0.713437] PCI: 0000:02:03.0 reg 14 io port: [c800, c8ff]
[    0.713487] pci 0000:02:03.0: PME# supported from D3hot D3cold
[    0.713494] pci 0000:02:03.0: PME# disabled
[    2.642539] serial 0000:02:03.0: PCI INT A -> Link[LNKF] -> GSI 5 (level, low) -> IRQ 5
[    2.647861] 0000:02:03.0: ttyS2 at I/O 0xc828 (irq = 5) is a 8250
[    2.650816] 0000:02:03.0: ttyS3 at I/O 0xc840 (irq = 5) is a 8250
[    2.651195] Couldn't register serial port 0000:02:03.0: -28

 The PCI slot 02:03.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 02:03.0:
	Modem chipset  detected on
NAME="Modem: ALi Corporation SmartLink SmartPCI563 56K Modem"
CLASS=0703
PCIDEV=10b9:545a
SUBSYS=201f:545a
IRQ=5
IDENT=slamr

 For candidate modem in:  02:03.0
   0703 Modem: ALi Corporation SmartLink SmartPCI563 56K Modem
      Primary device ID:  10b9:545a
 Support type needed or chipset:	slamr
 

----------------end Softmodem section --------------
The modem is supported by the Smartlink 
plus the slmodemd helper utility.  Read the
DOCs/Smartlink.txt and Modem/DOCs/YourSystem.txt for follow through guidance.


For 2.6.27-7-generic compiling drivers is necessary. As of October 2007 the current packages at
[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  are the
ungrab-winmodem-20070505.tar.gz and slmodem-2.9.11-20080126.tar.gz

Writing DOCs/Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.2
             and the compiler used in kernel assembly: 4.3.2


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.27-7-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.


Compressed files at: /usr/src/sl-modem.tar.bz2


If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 273064 2008-10-16 09:51 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

# start/stop the daemon when the USB modem is connected
KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   lrwxrwxrwx 1 root root 6 2009-01-01 19:55 /dev/modem -> ttySL0
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/030_sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/rules.d/030_sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
/etc/udev/sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/sl-modem-daemon.modutils:install slamr modprobe --ignore-install ungrab-winmodem ;  modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0) 
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by victan7300 on 2009-01-01
Please help me as the fax function is essential for my family, and if any offense due to my speech, I feel very sorry, but I am really tired of keep maintaining my previous Windows systems.

---

### Post by victan7300 on 2009-01-02
Anyone can help?

---

### Post by Aset on 2009-01-07
Try to use GCC 4.2 instead of 4.3.

---

