---
title: "Ubuntu Sees SoftModem as Audio Device"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by acer8930 on 2009-05-10
Ok, I was wondering why my Laptop with Ubuntu 9.04 wasn't playing any audio, and why I couldn't get my modem to be detected, so I was changing the Audio device under preferences, and these are my options:

Autodetect
HDA Intel NVIDIA HDMI (ALSA)
HDA Intel ALC889 Analog (ALSA)
HDA Intel ALC889 Analog (OSS)
HDA Intel ALC889 Analog (OSS)
ALSA - Advance Linux Sound Architecture
OSS - Open Sound Driver
PulseAudio Sound Server

So looking at ModemData.txt from scanModem, it appears that these options all apply to my modem, or that my modem and audio card are the same. My audio under Windows uses Realtek drivers, so IDK.

What do I do? 

Heres my ModemData.txt so you can see what I mean:

 [HTML]Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.28-11-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: http://www.linux.org/groups/index.html.
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
 scanModem update of:  2009_04_28

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
         snd_hda_intel       

Attached USB devices are:
 ID 064e:a117 Suyin Corp. 
 ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
 ID 138a:0001  
If a cellphone is not detected, see http://ubuntuforums.org/archive/index.php/t-878554.html

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to discuss@linmodems.org

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:293e	1025:0145	Audio device: Intel Corporation 82801I 

 Modem interrupt assignment and sharing: 
 22:       6642       6705   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[    0.499993] pci 0000:00:1b.0: reg 10 64bit mmio: [0xdb300000-0xdb303fff]
[    0.500041] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.500046] pci 0000:00:1b.0: PME# disabled
[   10.696227] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.696280] HDA Intel 0000:00:1b.0: setting latency timer to 64

 The PCI slot 00:1b.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to discuss@linmodems.org
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.19
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: ALC889 Analog : ALC889 Analog : playback 1 : capture 1
00-03: NVIDIA HDMI : NVIDIA HDMI : playback 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdb300000 irq 22

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: LSI ID 1040
Address: 1
Vendor Id: 0x11c11040
Subsystem Id: 0x10250145
Revision Id: 0x100200
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x11c11040
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
SUBSYS=1025:0145
IRQ=22
HDA=8086:293e
SOFT=8086:293e.HDA
CHIP=0x11c11040
IDENT=agrsm
Driver=agrsm

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801I 
      Primary device ID:  8086:293e
    Subsystem PCI_id  1025:0145 
    Softmodem codec or chipset from diagnostics: 0x11c11040
                               from    Archives: 
                        The HDA card softmodem chip is 0x11c11040
      

Support type needed or chipset:	agrsm


Writing DOCs/Intel.txt
      
   For 11c1:0260, 11c1:048c and 11c1:048f modem chips, try using the agrsm-20090418.tar.gz  
   at http://linmodems.technion.ac.il/packages/ltmodem/11c11040/

-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.3
             and the compiler used in kernel assembly: 4.3.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.28-11-generic/build

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
	-rwsr-xr-- 1 root dip 277352 2009-02-20 12:25 /usr/sbin/pppd

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
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------
[/HTML]

---

### Post by wpshooter on 2009-05-10
I would try (after first writing down all of the current parameter settings) changing your BIOS parameters to the default/fail safe settings and then see if the problem is possibly corrected and if not I would then attempt another installation of Ubuntu with the BIOS settings at the default parameters and I would do it from the ALTERNATE (text based) CD version of Ubuntu.

---

### Post by acer8930 on 2009-05-10
I will defaulting the BIOS parameters first.

And what do you mean by the text based CD version?

---

### Post by wpshooter on 2009-05-11
> **acer8930 said:**
> I will defaulting the BIOS parameters first.

And what do you mean by the text based CD version?

There is an ALTERNATE version of the Ubuntu installer (other than the live/desktop CD version) on which the installer is text based/non-graphical interface, this is one the install process only, once the O/S is installed you have the same Xserver that you do if you had installed from the live CD.

---

### Post by acer8930 on 2009-05-11
I'll google it, but how exactly do I use use it instead of the GUI installer?

---

### Post by wpshooter on 2009-05-11
> **acer8930 said:**
> I'll google it, but how exactly do I use use it instead of the GUI installer?

Basically, the same way, just boot to the CD, check the integrity first, then install from it.  Just a different look but supposed to do a somewhat better/more accurate job of the installation.

---

### Post by acer8930 on 2009-05-11
I'll give that a try later, I got the alternate version downloaded.

Thanks for the information. Even if it doesn't help right now, its good to know for the future.

---

### Post by mmoo9154 on 2009-06-06
I'm having this exact same problem with Ubuntu 9.04 an an Acer Aspire 8930 (has the same dvice set).

I would be very interested in any progress or even any failed results.

-Mark

---

### Post by acer8930 on 2009-06-06
I subscribed to the mailing list in the modem.txt. I haven't gotten a message in a while, but our drivers aren't supported on the current kernel version. It might work on older vesions of Ubuntu, but I didn't really feel like downgrading. Right now I've removed Ubuntu. I may try again later.

I guess the problem is the Modem is the same device as the Audio. The driver for the Audio also is what includes the functions for the modem, that why its detected as an Audio device. Since Realtek's drivers aren't open source, or neither is LSI's or Foxconn 's (different models have different chipsets), the drivers out now aren't realy specific enough for our configuration. Hopefully someday. I would like to get more involved in using linux, but its gonna have to wait.

---

