---
title: "Install a Lucnet dialup modem in 10.04 or 10.10"
date: 2010-11-26
forum: Hardware
---

### Post by aliirani on 2010-11-26
Hello all.
I have a dialup modem.
I want using this modem in ubuntu 10.04 or 10.10, Can i?(if yes, how?)
Output of scanmodem:
modedata:
```
 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.32-21-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: http://www.linux.org/groups/index.html.
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu ,  ALSA_version=1.0.21
Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010
 scanModem update of:  2010_05_29

Distrib_ID=Ubuntu
DistribCodeName=lucid
AptRepositoryStem=deb


Presently install your Linux Distributions dkms package. It provides for automated driver updates,
following upgrade of your kernel.  For details see http://linux.dell.com/projects.shtml#dkms

 There are no blacklisted modem drivers in /etc/modprobe*  files 

 Potentially useful modem drivers now loaded are:
                  

Attached USB devices are:
 ID 09da:000a A4 Tech Co., Ltd Port Mouse
 ID 047e:2892 Agere Systems, Inc. (Lucent) Systems Soft Modem
If a cellphone is not detected, see http://ubuntuforums.org/archive/index.php/t-878554.html
A sample report is:  http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html

Candidate PCI devices with modem chips are:
High Definition Audio cards can host modem chips.

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 001:
    Modem chipset  detected on
SLOT="Bus 001 Device 003:"
NAME="Agere Systems, Inc. (Lucent) Systems Soft Modem"
bus=001
USBmodemID=047e:2892
IDENT=agrsm
Driver=agrsm

For a detailed USB cellphone usage report, see http://linmodems.technion.ac.il/bigarch/archive-eighth/msg03240.html 
 For candidate modem in:  001
    Agere Systems, Inc. (Lucent) Systems Soft Modem
      Primary device ID:  047e:2892
 Support type needed or chipset:    agrsm
 


The AgereSystems/LSI agrsm code supports compiling of a agrmodem + agrserial driver pair.
There are a few different chipsets which use this driver pair, but they use different code resources:
Chipsets            KV*    PackageNames (most current as of November 2009)
----------------------------------------------------------------------------------------------
11c1:048c and 11c1:048f         2.6.29    agrsm048pci-2.1.60_20100108_i386.deb or agrsm048pci-2.1.60_20100108.tar.gz
11c1:0620                       2.6.31  agrsm06pci-2.1.80_20100106_i386.deb or agrsm06pci-2.1.80~20100106.tar.gz !!
11c11040 (on HDA audio cards)   2.6.31  agrsm-11c11040_20091225_i386.deb or agrsm-11c11040-2.1.80~20091225.tar.bz2  !!
   All available at: http://linmodems.technion.ac.il/packages/ltmodem/11c11040/   
Additionally there are;
automation & testing                    agrsm-tools_0.0.1_all.deb or agrsm-tools-0.0.1-2.noarch.rpm
General background                      agrsm_howto.txt 
------------------------------------------------------------------------------------------------
* KV == latest kernel release with a reported success 
!! Latest update with major credit to  Nikolay Zhuravlev
   But see conflict issue: http://linmodems.technion.ac.il/bigarch/archive-nineth/msg02753.html 
   For the 11c11040 chip with kernels 2.6.31 and later a change in a modules loading settingmay be necessary.
   Within the file /etc/modprobe.d/alsa-base.conf  (or equivalent for your Distro), change the phrase:
      options snd-hda-intel power_save=10
   to:
      options snd-hda-intel power_save=0
   or the agrsm drivers will not function. For Ubuntu related systems this can be done with:
   $ sudo gedit /etc/modprobe.d/alsa-base.conf

Report from  Bjorn Wielens:
Please note- trying to load the modules on a OpenSuSE 11.2 system gives
 an error about the module_version symbol. Using:
# modprobe --force agrmodem
# modprobe --force agrserial 
is necessary to load the drivers, and does not appear to cause ill effects.


All of the above packages are dkms competent.  This means that if your Linux distros dkms package
is previously installed, if provides for future updates matching forthcoming kernels.

-------------- end Agere Systems section -------------------


 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.4.3
             and the compiler used in kernel assembly: 4.4.3

 The patch utility is needed for compiling ALSA drivers, and possibly others. 

 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.4
   linuc_headers base folder /lib/modules/2.6.32-21-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at http://packages.ubuntu.com
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

Otherwise packages have to be found through http://packages.ubuntu.com
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
    -rwsr-xr-- 1 root dip 273312 2010-03-07 07:29 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html

To enable dialout without Root permission do:
    $ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
    sudo chmod a+x /usr/sbin/pppd

Checking settings of:    /etc/ppp/options
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
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

For guidance on FAX usage, get from http://linmodems.technion.ac.il/packages/  get faxing.tar.gz
It has samples for a modem using port /dev/ttySL0, which must be changed to match your modem's port.

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

```
scanout.001:```

bus=001
SLOT="Bus 001 Device 003:"
NAME="Agere Systems, Inc. (Lucent) Systems Soft Modem"
USBmodemID=047e:2892
IDENT=agrsm
Driver=agrsm
```
I guess my modem is a Lucent modem.

---

### Post by AlexanderDGreat on 2010-12-01
We have the same modem!

Any luck? As usual with Ubuntu you need LOTS OF LUCK.

---

### Post by aliirani on 2011-01-08
is there any chance to solve this problem?!
:(:(

---

