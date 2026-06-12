---
title: "Modem help - Toshiba Satellite L305D-S5934"
date: 2010-04-22
forum: Hardware
---

### Post by TeDiouS on 2010-04-22
Ubuntu 9.10
2.6.31-14

Toshiba Satellite L305D-S5934


I've downloaded the [hsf driver]("http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php"), installed, no go.
Installed the [alsa-driver]("http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86.php") w/ it as well, no go.
Installed the [Agere module/driver]("http://linmodems.technion.ac.il/packages/ltmodem/11c11040/"), no go...

Used the scan-tool, this is my ModemData.txt:
```
 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.31-14-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: http://www.linux.org/groups/index.html.
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu ,  ALSA_version=1.0.20
Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009
 scanModem update of:  2010_03_18
The modem symbolic link is /dev/modem -> ttySHSF0
Distrib_ID=Ubuntu
DistribCodeName=karmic
AptRepositoryStem=http://us.archive.ubuntu.com/ubuntu/


Presently install your Linux Distributions dkms package. It provides for automated driver updates,
following upgrade of your kernel.  For details see http://linux.dell.com/projects.shtml#dkms

 There are no blacklisted modem drivers in /etc/modprobe*  files 

 Potentially useful modem drivers now loaded are:
       snd_hda_intel           

Attached USB devices are:
 ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
 ID 04f2:b070 Chicony Electronics Co., Ltd 
 ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
If a cellphone is not detected, see http://ubuntuforums.org/archive/index.php/t-878554.html
A sample report is:  http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to discuss@linmodems.org

Candidate PCI devices with modem chips are:
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
High Definition Audio cards can host modem chips.

For candidate card in slot 00:14.2, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 00:14.2    1002:4383    1179:ff6a    Audio device: ATI Technologies Inc SBx00 Azalia 

 Modem interrupt assignment and sharing: 
 16:      33571        541   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:14.2 ----
[    0.671308] pci 0000:00:14.2: reg 10 64bit mmio: [0xd6400000-0xd6403fff]
[    0.671360] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.671366] pci 0000:00:14.2: PME# disabled
[    6.809990] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.810033] HDA Intel 0000:00:14.2: setting latency timer to 64
[    6.979696] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input8

 The PCI slot 00:14.2 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to discuss@linmodems.org
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: ALC268 Analog : ALC268 Analog : playback 1 : capture 1
00-02: ALC268 Analog : ALC268 Analog : capture 1

about /proc/asound/cards:
------------------------
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd6400000 irq 16

 PCI slot 00:14.2 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: LSI ID 1040
Address: 1
Function Id: 0x2
Vendor Id: 0x11c11040
Subsystem Id: 0x11790001
Revision Id: 0x100200
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x11c11040
If not a Conexant modem, the driver agrsm with its dependent drivers:

----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:14.2:
    Modem chipset  detected on
NAME="Audio device: ATI Technologies Inc SBx00 Azalia "
CLASS=0403
PCIDEV=1002:4383
SUBSYS=1179:ff6a
IRQ=16
HDA2=00:14.2
SOFT=1002:4383.HDA
HDAchipVendorID=11c1
CHIP=0x11c11040
IDENT=agrsm
Driver=agrsm

 For candidate modem in:  00:14.2
   0403 Audio device: ATI Technologies Inc SBx00 Azalia 
      Primary device ID:  1002:4383
    Subsystem PCI_id  1179:ff6a 
    Softmodem codec or chipset from diagnostics: 0x11c11040
                               from    Archives: 
                        The HDA card softmodem chip is 0x11c11040
      

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

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.4.1
             and the compiler used in kernel assembly: 4.4.1

 The patch utility is needed for compiling ALSA drivers, and possibly others. 

 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.4
   linuc_headers base folder /lib/modules/2.6.31-14-generic/build

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
    -rwsr-xr-x 1 root dip 277352 2009-02-20 09:25 /usr/sbin/pppd

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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 wlan0 wmaster0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   lrwxrwxrwx 1 root root 8 2010-04-22 12:01 /dev/modem -> ttySHSF0
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/00-hsf.rules:KERNEL=="ttySHSF0", SYMLINK="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/hsf.conflicts.conf:install snd-via82xx-modem /bin/true # temporarily disabled by hsf - conflicts with hsfmc97via
/etc/modprobe.d/hsf.conflicts.conf:install snd-atiixp-modem /bin/true # temporarily disabled by hsf - conflicts with hsfmc97ati
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/hsf.conf:alias /dev/modem /dev/ttySHSF
/etc/modprobe.d/hsf.conf:install /dev/ttySHSF /sbin/modprobe hsfpcibasic2; /sbin/modprobe hsfpcibasic3; /sbin/modprobe hsfmc97ich; /sbin/modprobe hsfmc97via; /sbin/modprobe hsfmc97ali; /sbin/modprobe hsfmc97ati; /sbin/modprobe hsfmc97sis; [ -e /lib/modules/`uname -r`/extra/hsfusbcd2.ko ] && /sbin/modprobe hsfusbcd2; /sbin/modprobe snd_hda_intel; [ -e /lib/modules/`uname -r`/extra/snd-hda-codec-hsfmodem.ko ] && /sbin/modprobe snd-hda-codec-hsfmodem; /bin/true
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:
/etc/modules.conf:alias /dev/modem /dev/ttySHSF
/etc/modules.conf:probeall /dev/ttySHSF hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_intel snd-hda-codec-hsfmodem
--------- end modem support lines --------

```And the wvdial output:
```
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: Input/output error
--> Cannot open /dev/modem: Input/output error
--> Cannot open /dev/modem: Input/output error

```I've read, and looked through many forums. No go...

If you have any information for me regarding this, please, let me know.

Thank you

---

### Post by TeDiouS on 2010-04-22
Once again... not even a point of direction.

Thank you all who at least tried.

Close please.

---

### Post by mockingbird on 2010-04-30
Why don't you read the entire file?

It says you need agrsm driver for LSI chip.  I know this because I have the same modem, and I wanted to check here if any progress was being made on an x64 version

If you're using x64 Ubuntu, you're out of luck.

Otherwise, follow the instructions here:

[http://linmodems.technion.ac.il/packages/ltmodem/11c11040/HOWTO-Agere-11c11040-HDA.html](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/HOWTO-Agere-11c11040-HDA.html)

And here's where you can download the packages:
[http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)

Good luck.

---

### Post by ANew on 2010-08-14
Have you been successfull in installing modem?

It seems the directory in .../packages/ltmodem/11l11040/
has a number of tar-files and deb-files for older
kernels and none for 10.04. Which tar-file is working?

---

### Post by ANew on 2010-08-14
> **mockingbird said:**
> 
And here's where you can download the packages:
[http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)

Good luck.

Which one? there seems to be no packages for new kernel.
Will the older tar-file work for new kernel?

---

### Post by mockingbird on 2010-10-22
> **ANew said:**
> Which one? there seems to be no packages for new kernel.
Will the older tar-file work for new kernel?

It should.  Download "agrsm-2.6.27-9-generic_2.6.27-9.14a_i386.deb" and then run "sudo dpkg -i agrsm-2.6.27-9-generic_2.6.27-9.14a_i386.deb".  If it doesn't work (Because it's for 2.6.2x" kernel), and you need the 2.6.3x kernel driver, download "agrsm-2.6.30.tar.bz2", run "tar -xjvf agrsm-2.6.30.tar.bz2" and look at the readme inside for instructions.

I didn't do any of this because I use x64 and not i386.

---

