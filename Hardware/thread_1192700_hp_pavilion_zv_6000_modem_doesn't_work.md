---
title: "hp pavilion zv 6000 modem doesn't work"
date: 2009-06-20
forum: Hardware
---

### Post by lukasoft on 2009-06-20
Hi all,
I've the trouble whit the  internal modem
Here post the modemdata from scan modem

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.28-11-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
 scanModem update of:  2009_05_31
The modem symbolic link is /dev/modem -> ttySL0
The slmodemd set symbolic link is /dev/ttySL0 -> /dev/pts/0
 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
                

Attached USB devices are:
 ID 04a9:2213 Canon, Inc. CanoScan LiDE 50/LiDE 35/LiDE 40
 ID 03ee:6901 Mitsumi SmartDisk FDD
 ID 072f:9000 Advanced Card Systems, Ltd ACR38 AC1038-based Smart Card Reader
 ID 1241:a325 Belkin 
 ID 13fd:0540 Initio Corporation 
 ID 040a:4103 Kodak Co. 
 ID 058f:9254 Alcor Micro Corp. Hub
 ID 1058:0702 Western Digital Technologies, Inc. Passport External HDD
 ID 0409:0058 NEC Corp. HighSpeed Hub
 ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
 ID 0ccd:0049 TerraTec Electronic GmbH 
 ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

For candidate card in slot 00:14.6, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:14.6	1002:4378	103c:3085	Modem: ATI Technologies Inc SB400 AC'97 Modem Controller 

 Modem interrupt assignment and sharing: 
 17:      21857   IO-APIC-fasteoi   radeon@pci:0000:01:05.0
 --- Bootup diagnostics for card in PCI slot 00:14.6 ----
[    0.541342] pci 0000:00:14.6: reg 10 32bit mmio: [0xb0003800-0xb00038ff]
[    1.957789] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.957797] serial 0000:00:14.6: PCI INT B disabled
[   25.976734] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  504.573187] ATI IXP MC97 controller 0000:00:14.6: PCI INT B disabled

 The PCI slot 00:14.6 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 


Packages needed for support of Advanced Linux Sound Architecture (ALSA) support should be installed: alsa-base and alsa-utilities!!
They are necessary for support of ALSA modem drivers, many Conexant chipset modems and success of modem diagnostics for modems requiring slmodemd actions.

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:14.6:
	Modem chipset  detected on
NAME="Modem: ATI Technologies Inc SB400 AC'97 Modem Controller "
CLASS=0703
PCIDEV=1002:4378
SUBSYS=103c:3085
IRQ=17
SOFT=1002:4378.MC97
CodecArchived=CXT
CodecClass=CXT
IDENT=hsfmodem
Driver=hsfmodem-drivers

 For candidate modem in:  00:14.6
   0703 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller 
      Primary device ID:  1002:4378
    Subsystem PCI_id  103c:3085 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: CXT, a Conexant type using hsfmodem software.
      CXTnn is  a generic for all CXTnumbers, with  Linuxant hsfmodem software support.                  
      

Support type needed or chipset:	hsfmodem


For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt


Start at [http://www.linuxant.com/drivers/hsf/downloads-license.php](http://www.linuxant.com/drivers/hsf/downloads-license.php) to find the
hsfmodem package matching your System. For several Linux distros, there are
precompiled drivers matched to specific kernels. These have within the FileName,
your KernelVersion:	2.6.28_11_generic
They can be found through [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) 
A more precise location may be given a few paragraphs below.
If an EXACT Match with your your KernelVersion is not found, one of the 
"Generic packages with source" near the bottom of the page must be used.
Downloaded packages must be moved into the Linux partition (home folder is OK)
and unzipped with:
	unzip hsf*.zip
The installation command for a .deb suffic packages is, with root/adm permission:
  sudo dpkg -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm
 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.80.02.02full_k2.6.28_11_generic_ubuntu_i386.deb.zip 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.
 
 Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.3
             and the compiler used in kernel assembly: 4.3.3

 The patch utility is needed and is needed for compiling ALSA drivers, and possibly others. 

 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.28-11-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




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
	-rwsr-xr-x 1 root dip 277352 2009-02-20 18:25 /usr/sbin/pppd

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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 wlan0 wmaster0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   lrwxrwxrwx 1 root root 6 2009-06-07 15:35 /dev/modem -> ttySL0
slmodemd created symbolic link /dev/ttySL0:  lrwxrwxrwx 1 root root 10 2009-06-07 15:35 /dev/ttySL0 -> /dev/pts/0
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------
this modem i can't test it and i think something i need to set to used it whit efax gtk
please help me:confused::confused:

---

### Post by Ayuthia on 2009-06-20
The results look like they are telling you that you have a Conexant modem.  This means that you will have to install a package from Linuxant to make it work:
```
Start at http://www.linuxant.com/drivers/hsf/...ds-license.php to find the
hsfmodem package matching your System. For several Linux distros, there are
precompiled drivers matched to specific kernels. These have within the FileName,
your KernelVersion: 2.6.28_11_generic
They can be found through http://www.linuxant.com/drivers/hsf/full/downloads.php
A more precise location may be given a few paragraphs below.
If an EXACT Match with your your KernelVersion is not found, one of the
"Generic packages with source" near the bottom of the page must be used.
Downloaded packages must be moved into the Linux partition (home folder is OK)
and unzipped with:
unzip hsf*.zip
The installation command for a .deb suffic packages is, with root/adm permission:
sudo dpkg -i hsf*.deb
while for .rpm suffix it is, with:
rpm -i hsf*.rpm
From http://www.linuxant.com/drivers/hsf/...ubuntu-x86.php
download hsfmodem-7.80.02.02full_k2.6.28_11_generic_ubuntu_i386.deb. zip
Under Linux unpack with:
$ unzip hsfmodem*.zip
Then install with:
$ sudo dpkg -i hsfmodem*.deb
Subsequently, the modem should be found with
$ sudo wvdialconf /etc/wvdial.conf
Edit in your personal information with:
$ sudo gedit /etc/wvdial.conf
and try dialing out with:
$ sudo wvdial.
See DOCs/Testing.txt for details.

Read DOCs/Conexant.txt
```
Just to let you know, there is a cost if you want it to be capable of 56k speeds.  Otherwise it will run at 14.4k

---

