---
title: "Install winmodem AGRSM, Ubuntu Server &quot;8.04.1&quot;"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2009-04-08
Hello every one,

I have few problems getting my modem installed. I connect to the Internet by dial-up, through modem. So I have a Toshiba Satellite A200 with an AGRSM modem. 
can anyone help me with this... PLEASE. 

I appreciate any help.

Here is the output of 

> $ sudo ./scanModem
$ gedit ModemData.txt 


 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-21-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008
 scanModem update of:  2008_08_26

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 1058:1100 Western Digital Technologies, Inc. 
 ID 04f2:b008 Chicony Electronics Co., Ltd 

USB modems not recognized

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 00:1b.0    8086:284b    1179:ff00    Audio device: Intel Corporation 82801H 

 Modem interrupt assignment and sharing: 
 22:        399        393   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   40.492837] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   40.492870] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.16
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-04: ALC268 Analog : ALC268 Analog : capture 1
00-00: ALC268 Analog : ALC268 Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc500000 irq 22

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: Generic 11c1 ID 1040
Address: 1
Vendor Id: 0x11c11040
Subsystem Id: 0x11790001
Revision Id: 0x100200
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x11c11040
If not a Conexant modem, the driver agrmodem+agrserial+patched_snd-hda-intel with its dependent drivers:

----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:1b.0:
    Modem chipset  detected on
NAME="Audio device: Intel Corporation 82801H "
CLASS=0403
PCIDEV=8086:284b
SUBSYS=1179:ff00
IRQ=22
HDA=8086:284b
SOFT=8086:284b.HDA
CHIP=0x11c11040
IDENT=11c11040
Driver=agrmodem+agrserial+patched_snd-hda-intel

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801H 
      Primary device ID:  8086:284b
    Subsystem PCI_id  1179:ff00 
    Softmodem codec or chipset from diagnostics: 0x11c11040
                               from    Archives: 
                        The HDA card softmodem chip is 0x11c11040
      

Support type needed or chipset:    11c11040

----------------end Softmodem section --------------

Writing DOCs/Intel.txt

 Vendor 11c1 is Lucent Technologies with modem technology now under LSI Inc. 
Their Linux  code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its 
 continued maintenance is only initiated at the request of a major chipset buyer,
 or comparable sponsor. Several different  modem chipset types  are produced: 
 with varying support under Linux.
 Device ID   Support        Name           Comment
 ---------   -------------  -----------    -----------------------------
 0480        serial_drivers Venus           controller chipset 1673JV7
 0440-045d   martian        Mars/Apollo     DSP (digital signal processing) chipsets
 0462        none           56K.V90/ADSL Wildwire 
 048d none                   SV2P            soft modem 
 048(c or f) AGRSM          SV2P            soft modem
 0600        none           soft modem, very few in the field.
 0620        AGRSM          Pinball  soft modem, in some HP desktop PCs
 011c11040   AGRSM          hosted on High Definition Audio cards
 062(1-3)    none           SV92PP,Pinball  soft modem, in some HP desktop PCs

martian - At [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/)
AGRSM - At [http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)
  Compiling resources for a driver module pair: agrmodem.ko + agrserial.ko
  Use the  agrsm-HDA-20080721-ALSA15.tar.bz2 or agrsm-HDA-20080721.tar.bz2
  Read the agrsm_howto.txt.  For 11c11040 chips, also the HOWTO-Agere-11c11040-HDA.html

-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.2.3
             and the compiler used in kernel assembly: 4.2.4


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.2
   linuc_headers base folder /lib/modules/2.6.24-21-generic/build

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
    -rwsr-xr-- 1 root dip 269256 2007-10-04 15:57 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

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
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 vmnet1 vmnet8
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

---

