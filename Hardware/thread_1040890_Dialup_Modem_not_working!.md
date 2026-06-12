---
title: "Dialup Modem not working!"
date: 2009-01-16
forum: Hardware
---

### Post by scoopy on 2009-01-16
Hi there friends

I'm having a problem with getting my dialup modem to work:

Info this is my modemData.txt file from scanModem

```
 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.27-9-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: http://www.linux.org/groups/index.html.
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008
 scanModem update of:  2009_01_11

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 The /proc/asound/ audio+modem diagostics are being copied.
Attached USB devices are:
 ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
If a cellphone is not detected, see http://ubuntuforums.org/archive/index.php/t-878554.html

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to discuss@linmodems.org

For candidate card in slot 00:10.1, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:10.1	10de:026c	103c:30b7	Audio device: nVidia Corporation MCP51 High Definition Audio 

 Modem interrupt assignment and sharing: 
 21:       5321    2955659   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:10.1 ----
[    0.605050] PCI: 0000:00:10.1 reg 10 32bit mmio: [b0000000, b0003fff]
[    0.605083] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.605088] pci 0000:00:10.1: PME# disabled
[    1.840203] pci 0000:00:10.1: Enabling HT MSI Mapping
[   20.651416] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[   20.651451] HDA Intel 0000:00:10.1: setting latency timer to 64

 The PCI slot 00:10.1 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to discuss@linmodems.org
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.18
The modem cards detected by "aplay -l"  are: 
card 0: NVidia [HDA NVidia], device 6: Conexant HSF Modem [Conexant HSF Modem]

The /proc/asound/pcm file reports:
-----------------------
00-00: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1
00-01: Conexant Digital Audio : Conexant Digital Audio : playback 1
00-06: Conexant HSF Modem : Conexant HSF Modem : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xb0000000 irq 21

 PCI slot 00:10.1 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.27-9-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko

Modem data is not obvious in the /proc/asound/ files 
which have been copied to Modem/ALSAluke.tgz.
Please send this file to scanModem maintainer:
	marvin.stodolsky@gmail.com

If not a Conexant modem, the driver snd-hda-intel with its dependent drivers:
snd_hda_intel         452648  2 
snd_pcm                83716  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         16776  2 snd_hda_intel,snd_pcm
snd_hwdep              15492  1 snd_hda_intel
snd                    67108  14 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:10.1:
	Modem chipset  detected on
NAME="Audio device: nVidia Corporation MCP51 High Definition Audio "
CLASS=0403
PCIDEV=10de:026c
SUBSYS=103c:30b7
IRQ=21
HDA=10de:026c
SOFT=10de:026c.HDA
ArchivedChip=0x14f12bfa
CodecClass=14f1
IDENT=hsfmodem
SLMODEMD_DEVICE=hw:0,6
Driver=hsfmodem-drivers

 For candidate modem in:  00:10.1
   0403 Audio device: nVidia Corporation MCP51 High Definition Audio 
      Primary device ID:  10de:026c
    Subsystem PCI_id  103c:30b7 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 0x14f12bfa
                        
      

Support type needed or chipset:	hsfmodem


For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt


Start at http://www.linuxant.com/drivers/hsf/downloads-license.php to find the
hsfmodem package matching your System. For several Linux distros, there are
precompiled drivers matched to specific kernels. These have within the FileName,
your KernelVersion:	2.6.27_9_generic
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

Support for Conexant chips hosted on High Definition Audio cards may require
installation of additional packages, one of the alsa-driver-linuxant packages
on  http://www.linuxant.com/alsa-driver/  At the same time download the 
alsa-driver-1.0.17-1.patch , in case it prove to be later needed. During the
hsfmodem install, there will be a message if there is necessary installation of
alsa-driver-linuxant

The installation command for a .deb suffic packages is, with root/adm permission:
  sudo alsa* -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm

There may a message that "Dependencies" are not satisfied.  In this case the Ubuntu/Debian packages to be installed are linux-libc-dev & libc6-dev. Package
names may be different for other Linuxes. If not on your install CD, these
packages can be searched for at http://packages.ubuntu.com.  After download,
they can be coinstalled with:
	sudo dpkg -i li*.deb
Again try the alsa-driver-linuxant

There may be a message that the patch must be applied.  In this case get the
ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2 
Under Linux, this package is unpacked with:
$ tar jxf alsa*.tar.bz2
Next the patch is applied with:
$ patch -p0 < alsa-driver-1.0.17-1.patch

See http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html
for details on compiling and installing replacement snd-hda-intel + its
dependent drivers.
After the installation is completed, rerun the hsfmodem installation.
Reboot and try to detect the modem with Root permission:
	sudo wvdialconf  /etc/wvdial.conf

 From  http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php
 download hsfmodem-7.80.02.01full_k2.6.27_9_generic_ubuntu_i386.deb.zip 
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

 Versions adequately match for the compiler installed: 4.3.2
             and the compiler used in kernel assembly: 4.3.2


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.27-9-generic/build

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
	-rwsr-xr-- 1 root dip 277160 2008-11-21 09:58 /usr/sbin/pppd

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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 wlan0 wmaster0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

```

I've downloaded and install the driver from here that matches my kernel [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php), installed Gnome ppp and get this error when running in sudo:

```
WVCONF: /root/.wvdial.conf
GNOME PPP: STDOUT: Editing `/dev/null'.
GNOME PPP: STDERR: Modem Port Scan<*1>: S0   S1   S2   S3   
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Scanning your serial ports for a modem.
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Sorry, no modem was detected!  Is it in use by another program?
GNOME PPP: STDOUT: Did you configure it properly with setserial?
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Please read the FAQ at http://open.nit.ca/wiki/?WvDial
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
GNOME PPP: Connecting...
GNOME PPP: STDERR: --> Ignoring malformed input line: ";Do NOT edit this file by hand!"
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.60
GNOME PPP: STDERR: --> Cannot open /dev/modem: No such file or directory
GNOME PPP: STDERR: --> Cannot open /dev/modem: No such file or directory
GNOME PPP: STDERR: --> Cannot open /dev/modem: No such file or directory
GNOME PPP: Unable to KILL wvdial process!

```

I think that's it.

Any suggestions?  

Thanks

Scoopy

---

### Post by scoopy on 2009-01-17
so why hasn't anyone replied to my question?  is it because I wear glasses?

:(

---

