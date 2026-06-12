---
title: "agere modem driver"
date: 2008-12-07
forum: Hardware
---

### Post by a.dehqan on 2008-12-07
In The Name Of God;
Hello;

i'll be thankfull if you guide me ;
laptop hp 1040 , this is result of scanmodem:

```
 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-16-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: http://www.linux.org/groups/index.html.
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=x86_64,  
Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008
 scanModem update of:  2008_07_21


Some modem drivers can only be used in 32 bit modem on x86_64 systems,
while some others are competent on x86_64 Systems.  Cases are:
1) http://linmodems.technion.ac.il/bigarch/archive-seventh/msg03119.html 
for the snd-hda-intel audio+modem driver. Also applicable to AC97 modem controllers.
In both cases, 32 bit libraries must be installed to support the slmodemd helper having a precompiled 32 bit component.
2) For USB modems using the slusb.ko driver. 32 bit libraries must be installed to support the slmodemd helper having a precompiled 32 bit component
3) The hsfmodem and hcflinmodem drivers for Conexant chipsest modes are x86_64 competent.

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 03f0:171d Hewlett-Packard 
 ID 09da:000a A4 Tech Co., Ltd 
 ID 5986:0137 Bison 
 ID 058f:6387 Alcor Micro Corp. Transcend JetFlash 110 USB 2.0 Flash Drive (2GB)

USB modems not recognized

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:293e	103c:3603	Audio device: Intel Corporation 82801I 

 Modem interrupt assignment and sharing: 
 22:        434        443   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   30.763639] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   30.764490] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
 New HDA card type: 
    
    


The ALSA verion is 1.0.15
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-01: STAC92xx Digital : STAC92xx Digital : playback 1
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 2

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdf300000 irq 22

Modem support under STAC92xx audio card hosts may require upgrade
of snd-hda-intel + its dependent drivers to ALSA version  1.0.16.
The following modem only worked after the upgrade from to 1.0.16 from 1.0.14
 PCI ID      SubsystemID     Name
 ---------   ---------       --------------
 8086:27d8   107b:0366       Audio device: Intel Corporation 82801G
with ALSA diagnostics
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 2
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
       Codec: Motorola Si3054
            for 107b:0366 hosted modem chip: 0x10573057

For a standard Ubuntu system needed to support the driver compilation were

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

A candidate modem is not evident among the PCI devices:
------------------------------------------------
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e8 (rev a1)
02:00.0 Network controller: Intel Corporation Unknown device 4237
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. Unknown device 2380
06:00.1 System peripheral: JMicron Technologies, Inc. Unknown device 2382
06:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
06:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
06:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384
------------------------------------------------
 with USB and bridge devices not displayed.

 If your modem is connected by an external serial cable,
 or mounted internally on an ISA card, scanModem would not access it. 
 Try with Root permission
 $ sudo wvdialconf  /etc/wvdial.conf
 to detect these modem types and some USB modems.
 If the detection is successful, read the DOCs/wvdial.txt .
 Edit the /etc/wvdial.conf with Root permission:
 	sudo  gedit  /etc/wvdial.conf
  will be able to dial out with Root permission:
	sudo wvdial

 Many modems for which scanModem fails have Conexant chips. 
 From http://www.linuxant.com/drivers/modemident.php
 get the ListModem tool, which will report on Conexant chipset modems

 If the above tests fail, please provide any independent information available on your modem.
 If an alternative boot into Microsoft windows can be done, do mouse
clicks on:
   Start > Settings > Control Panel > Classical View (for Window XP) > System
> Hardware > Device Manager > Modems > Click on the + > Modem. Double click to
expand the graphic. Manufacturer information may be displayed. For example, CXT
stands for Conexant. Click the Diagnostics Tab. Record any hardware ID or vendor
and device information. From the Driver Details TAB, copy out the VENdor and DEVice information.
Next do the Query Modem and record the ATI specifications displayed such as:
    ATI3 - Agere SoftModem Version 2.1.22
    ATI5 - 2.1.22, AMR Intel MB, AC97 ID:SIL REV:0x27
Try to identify the modem setup file, with name perhaps MODEM.INF.
If may contain chipset Vendor informaton.

 The /proc/asound/ audio+modem diagostics are being copied.
 Finished copy to Modem/ALSAroot.tgz

Predictive diagnostics for card in bus 00:1b.0:
	Modem chipset not detected on
NAME="Audio device: Intel Corporation 82801I "
CLASS=0403
PCIDEV=8086:293e
SUBSYS=103c:3603
IRQ=22

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801I 
      Primary device ID:  8086:293e
 Support type needed or chipset:	
 

----------------end Softmodem section --------------

scanModem could not identify the Support Type needed from diagnosics or archives.
	If an alternative boot into Microsoft windows can be done, do mouse
clicks on:
   Start > Settings > Control Panel > Classical View (for Window XP) > System
> Hardware > Device Manager > Modems > Click on the + > Modem. Double click to
expand the graphic. Manufacturer information may be displayed. For example, CXT
stands for Conexant. Click the Diagnostics Tab. Record any hardware ID or vendor
and device information.
Next do the Query Modem and record the ATI specifications displayed such as:
    ATI3 - Agere SoftModem Version 2.1.22
    ATI5 - 2.1.22, AMR Intel MB, AC97 ID:SIL REV:0x27
Try to identify the modem setup file, with name perhaps MODEM.INF.
If may contain chipset Vendor informaton.


Writing DOCs/Intel.txt


 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.2.3
             and the compiler used in kernel assembly: 4.2.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.2
   linuc_headers base folder /lib/modules/2.6.24-16-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are n. The also required headers of package libc6 are commonly installed by default. 
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
	-rwsr-xr-- 1 root dip 313600 2007-10-05 00:18 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html

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
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

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
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

```

lspci does not show modem ...
But in vista modem is detected "agera systems HDA".

Any opinion ?

regards dehqan

---

