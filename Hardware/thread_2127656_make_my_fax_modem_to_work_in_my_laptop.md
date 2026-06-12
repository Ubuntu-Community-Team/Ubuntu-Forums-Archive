---
title: "make my fax modem to work in my laptop"
date: 2013-03-20
forum: Hardware
---

### Post by vahidreza.y on 2013-03-20
Hi,

i am a newbie in ubuntu (generally linux based systems) and is about 2 months migerated to ubuntu.
everything is fine except i need to use my laptop fax modem to send and receive faxes, after a little search i found wow it is is not as easy as pie !

ok i know the followings :
i have a  acer 5738 laptop with Modem: 56K ITU V.92 with PTT approval, Wake-on-Ring ready according to this [link]("http://panam.acer.com/acerpanam/notebook/2009/acer/aspire/Aspire5738/Aspire5738sp2.shtml").
i downloaded scanModem and ModemData.txt is as follow :
```
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu ,  ALSA_version=1.0.24
Linux version 3.2.0-38-generic-pae (buildd@panlong) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #61-Ubuntu SMP Tue Feb 19 12:39:51 UTC 2013
 scanModem update of:  2011_08_08

Distrib_ID=Ubuntu
DistribCodeName=precise
AptRepositoryStem=http://archive.ubuntu.com/ubuntu


Presently install your Linux Distributions dkms package. It provides for automated driver updates,
following upgrade of your kernel.  For details see http://linux.dell.com/projects.shtml#dkms

 There are no blacklisted modem drivers in /etc/modprobe*  files 

 Potentially useful modem drivers now loaded are:
       snd_hda_intel           

Attached USB devices are:
 ID 1c6b:a222 Philips & Lite-ON Digital Solutions Corporation DVD Writer Slimtype eTAU108
 ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
 ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
 ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
 ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
If a cellphone is not detected, see http://ubuntuforums.org/archive/index.php/t-878554.html
A sample report is:  http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to discuss@linmodems.org

Candidate PCI devices with modem chips are:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
High Definition Audio cards can host modem chips.

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 00:1b.0    8086:293e    1025:0205    Audio device: Intel Corporation 82801I 

 Modem interrupt assignment and sharing: 
 46:        988        253   PCI-MSI-edge      snd_hda_intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[    0.298057] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.298077] pci 0000:00:1b.0: reg 10: [mem 0xf4700000-0xf4703fff 64bit]
[    0.298158] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.298163] pci 0000:00:1b.0: PME# disabled
[   11.552609] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
[   11.552616] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
[   11.552636] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.552694] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   11.552722] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   11.755709] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   11.755822] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.755905] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   11.755988] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13

 The PCI slot 00:1b.0 of the modem card may be disabled early in 
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
00-00: ALC888 Analog : ALC888 Analog : playback 1 : capture 1
00-01: ALC888 Digital : ALC888 Digital : playback 1
00-02: ALC888 Analog : ALC888 Analog : capture 1
00-03: HDMI 0 : HDMI 0 : playback 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf4700000 irq 46

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/3.2.0-38-generic-pae/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.2.0-36-generic-pae/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: LSI ID 1040
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x11c11040
Subsystem Id: 0x11c10001
Revision Id: 0x100200
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x11c11040

The softmodem chip 11c11040 is hosted on the Subsytem of the High Definition Audio card,
and is supported by the AgereSystems/LSI driver pair agrmodem + agrserial, which is provided by 
the most current package agrsm-11c11040-version at http://linmodems.technion.ac.il/packages/ltmodem/11c11040/ 

If not a Conexant modem, the driver agrsm with its dependent drivers:

----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:1b.0:
    Modem chipset  detected on
NAME="Audio device: Intel Corporation 82801I "
CLASS=0403
PCIDEV=8086:293e
SUBSYS=1025:0205
IRQ=46
HDA2=00:1b.0
SOFT=8086:293e.HDA
HDAchipVendorID=11c1
CHIP=0x11c11040
IDENT=agrsm
Driver=agrsm
package=agrsm-11c11040

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801I 
      Primary device ID:  8086:293e
    Subsystem PCI_id  1025:0205 
    Softmodem codec or chipset from diagnostics: 0x11c11040
                               from    Archives: 
                        The HDA card softmodem chip is 0x11c11040
      

Support type needed or chipset:    agrsm


Writing DOCs/Intel.txt

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

 Versions adequately match for the compiler installed: 4.6.3
             and the compiler used in kernel assembly: 4.6

 linux-headers-3.2.0-38-generic-pae resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
     linux-headers-3.2.0-38-generic-pae


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
    -rwsr-xr-- 1 root dip 273272 Feb  4  2011 /usr/sbin/pppd

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
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

For guidance on FAX usage, get from http://linmodems.technion.ac.il/packages/  get faxing.tar.gz
It has samples for a modem using port /dev/ttySL0, which must be changed to match your modem's port.

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 ppp0
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

ok, i downloaded "agrsm-11c11040_20091225_i386.deb" and installed it according to what ModemData.txt did output.
also downloaded "agrsm-tools_0.0.1_all.deb" and installed it for automation & testing as suggested !

i tried to use agrsm-test for instructions in /Docs/Agrsm.txt and the output is :
```
The agrsm drivers not found for boot kernel 3.2.0-38-generic-pae .
 Were they installed for a different kernel version?
 Checking all installed module trees:


    Exiting

```

what hell of a complicated task it is.
anyway is there some one can help me ?

---

