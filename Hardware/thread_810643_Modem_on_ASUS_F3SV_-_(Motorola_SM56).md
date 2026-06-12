---
title: "Modem on ASUS F3SV - (Motorola SM56)"
date: 2008-05-28
forum: Hardware
---

### Post by mahmoos.sajjadi on 2008-05-28
:( Hi
I'm Very new User in linux and not familier with english and linux
please help me with siples words and step by step!

after many try to install Modem in my laptop(ASUS FS3V with Motorola SM56 winmodem)
i finaly find scanModem and run it


this file made a folder (Modem) with many files
one of them (ModemData.txt):

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-16-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Your contry's local Linux experts
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html). 
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
 scanModem update of:  2008_05_02

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 07ca:a301 AVerMedia Technologies, Inc. 
 ID 174f:6a33  
 ID 046d:c019 Logitech, Inc. 

USB modems not recognized
For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:284b	1043:1339	Audio device: Intel Corporation 82801H 

 Modem interrupt assignment and sharing: 
 23:       9365       9416   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   22.748353] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   22.748370] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.
 PCI slot 00:1b.0 has a High Definition Audio Card

The ALSA verion is 1.0.15
The modem cards detected by "aplay -l"  are:
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

The /proc/asound/pcm file reports:
-----------------------
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-00: ALC861VD Analog : ALC861VD Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 23
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: Motorola Si3054
Address: 1
Vendor Id: 0x10573055
Subsystem Id: 0x10431316
Revision Id: 0x100700
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x10573055

The softmodem chip 0x10573055 is in principle supported by the COMM support of slmodemd 
and the joint snd-hda-intel audio+modem driver, begun with ALSA version 1.0.13.  
For HDA cards with ALC883 chips, an upgrade to ALSA verions 1.0.15 way be necessary. Instructions for upgrading snd-hda-intel and its dependent driver set are at: [http://linmodems.technion.ac.il/archive-seventh/msg00282.html](http://linmodems.technion.ac.il/archive-seventh/msg00282.html)

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 00:1b.0:
	Modem chipset  detected on
CLASS="Class 0403: 8086:284b"
NAME="Audio device: Intel Corporation 82801H "
SUBSYS=1043:1339
PCIDEV=8086:284b
IRQ=23
HDA=8086:284b
SOFT=8086:284b.HDA
CodecArchived=10573055
CHIP=0x10573055
IDENT=slmodemd
SLMODEMD_DEVICE=hw:0,6
Driver=snd-hda-intel

 For candidate modem in:  00:1b.0
   Class 0403: 8086:284b Audio device: Intel Corporation 82801H 
      Primary device ID:  8086:284b
    Subsystem PCI_id  1043:1339 
    Softmodem codec or chipset from diagnostics: 0x10573055
                               from    Archives: 0x10573055, residing on a HDA Subsystem with support by slmodemd and driver snd-hda-intel
                        The HDA card softmodem chip is 0x10573055
      

Support type needed or chipset:	slmodemd supporting the snd-hda-intel audio+modem driver

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD.gcc4.2.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD.gcc4.2.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

----------------end Softmodem section --------------

Writing Intel.txt
Writing Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.2.3
             and the compiler used in kernel assembly: 4.2.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.2
   linuc_headers base folder /lib/modules/2.6.24-16-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default. When compiling ALSA drivers, the utility "patch" will also be needed.



If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed package
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269256 2007-10-04 23:27 /usr/sbin/pppd

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

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
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



====================================================


I send it to [email]Discuss@Linmodems.org[/email] and he replied to me this message :


do as scanModem suggests:
<quote>
Support type needed or chipset: slmodemd supporting the snd-hda-intel
audio+modem driver

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
 the package SLMODEMD.gcc4.2.tar.gz having a compiled slmodemd. Unpack
under Linux with:
       $ tar zxf SLMODEMD.gcc4.2.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
       sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6
 reporting dynamic creation of ports:
       /dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.
</quote>
Regards,

Antonio

On 5/27/08, [email]m.sajjadi@aut.ac.ir[/email] <m.sajjadi@aut.ac.ir> wrote:
>  Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
>  as HTML can contain viruses. Use as the email Subject Line:
>           YourName, YourCountry  kernel 2.6.24-16-generic
>  With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
>  YourCountry will enable Country specific guidance. Your contry's local Linux experts
>  can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
> They will know your Country's modem code, which may be essential for dialup service.
> Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
>  So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org)
> --------------------------  System information ----------------------------
> CPU=i686,
> Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
>  scanModem update of:  2008_05_02
>
>  There are no blacklisted modem drivers in /etc/modprobe*  files
> Attached USB devices are:
>  ID 07ca:a301 AVerMedia Technologies, Inc.
>  ID 174f:6a33
>  ID 046d:c019 Logitech, Inc.
>
> USB modems not recognized
> For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
>  PCI slot       PCI ID          SubsystemID     Name
>  ----------     ---------       ---------       --------------
>  00:1b.0        8086:284b       1043:1339       Audio device: Intel Corporation 82801H
>
>  Modem interrupt assignment and sharing:
>  23:       9365       9416   IO-APIC-fasteoi   HDA Intel
>  --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
> [   22.748353] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
> [   22.748370] PCI: Setting latency timer of device 0000:00:1b.0 to 64
>
>
> ===== Advanced Linux Sound Architecture (ALSA) diagnostics =====
> The ALSA packages provide audio support and also drivers for some modems.
> ALSA diagnostics are written during bootup to /proc/asound/ folders.
>  PCI slot 00:1b.0 has a High Definition Audio Card
>
> The ALSA verion is 1.0.15
> The modem cards detected by "aplay -l"  are:
> card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
>
> The /proc/asound/pcm file reports:
> -----------------------
> 00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
> 00-00: ALC861VD Analog : ALC861VD Analog : playback 1 : capture 1
>
> about /proc/asound/cards:
> ------------------------
>  0 [Intel          ]: HDA-Intel - HDA Intel
>                      HDA Intel at 0xfebf8000 irq 23
>  The modem codec file for the HDA card is: /proc/asound/card0/codec#1
> --------------------------------------------------------
> Codec: Motorola Si3054
> Address: 1
> Vendor Id: 0x10573055
> Subsystem Id: 0x10431316
> Revision Id: 0x100700
> Modem Function Group: 0x1
>
>  The audio card hosts a softmodem chip:  0x10573055
>
> The softmodem chip 0x10573055 is in principle supported by the COMM support of slmodemd
> and the joint snd-hda-intel audio+modem driver, begun with ALSA version 1.0.13.
> For HDA cards with ALC883 chips, an upgrade to ALSA verions 1.0.15 way be necessary. Instructions for upgrading snd-hda-intel and its dependent driver set are at: [http://linmodems.technion.ac.il/archive-seventh/msg00282.html](http://linmodems.technion.ac.il/archive-seventh/msg00282.html)
>
> === Finished firmware and bootup diagnostics, next deducing cogent software. ===
>
> Predictive diagnostics for card in bus 00:1b.0:
>        Modem chipset  detected on
> CLASS="Class 0403: 8086:284b"
> NAME="Audio device: Intel Corporation 82801H "
> SUBSYS=1043:1339
> PCIDEV=8086:284b
> IRQ=23
> HDA=8086:284b
> SOFT=8086:284b.HDA
> CodecArchived=10573055
> CHIP=0x10573055
> IDENT=slmodemd
> SLMODEMD_DEVICE=hw:0,6
> Driver=snd-hda-intel
>
>  For candidate modem in:  00:1b.0
>   Class 0403: 8086:284b Audio device: Intel Corporation 82801H
>      Primary device ID:  8086:284b
>    Subsystem PCI_id  1043:1339
>    Softmodem codec or chipset from diagnostics: 0x10573055
>                               from    Archives: 0x10573055, residing on a HDA Subsystem with support by slmodemd and driver snd-hda-intel
>                        The HDA card softmodem chip is 0x10573055
>
>
> Support type needed or chipset: slmodemd supporting the snd-hda-intel audio+modem driver
>
>  An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
>  provides Low Level support enabling contact with the modem hardware.
>  For all BUT Conexant chip soft modems (using hsfmodem software)
>  complementary High Level support is through a Smartlink utility:  slmodemd
>
>  Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
>  the package SLMODEMD.gcc4.2.tar.gz having a compiled slmodemd. Unpack under Linux with:
>        $ tar zxf SLMODEMD.gcc4.2.tar.gz
>  and read instructions therein. But briefly, the modem is setup with command:
>        sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6
>  reporting dynamic creation of ports:
>        /dev/ttySL0 --> /dev/pts/N   , with N some number
>  Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.
>
> ----------------end Softmodem section --------------
>
> Writing Intel.txt
> Writing Smartlink.txt
> ============ end Smartlink section =====================
>
>  Completed candidate modem analyses.
>
>  The base of the UDEV device file system is: /dev/.udev
>
>  Versions adequately match for the compiler installed: 4.2.3
>             and the compiler used in kernel assembly: 4.2.3
>
>
>
>  Minimal compiling resources appear complete:
>   make utility - /usr/bin/make
>   Compiler version 4.2
>   linuc_headers base folder /lib/modules/2.6.24-16-generic/build
>
>  However some compilations and executable functions may need additional files,
>  in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
>  For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default. When compiling ALSA drivers, the utility "patch" will also be needed.
>
>
>
> If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
> Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
> and any of its dependents, under Ubuntu linux-libc-dev
>
> If an alternate ethernet connection is available,
> $  apt-get update
> $  apt-get -s install linux-kernel-devel
> will install needed package
> For Debian/Ubuntu related distributions, run the following command to display the needed package list:
>
> Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
> Once downloaded and transferred into a Linux partition,
> they can be installed alltogether with:
> $ sudo dpkg -i *.deb
>
>
> Checking pppd properties:
>        -rwsr-xr-- 1 root dip 269256 2007-10-04 23:27 /usr/sbin/pppd
>
> In case of an "error 17" "serial loopback" problem, see:
>    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)
>
> To enable dialout without Root permission do:
>        $ su - root  (not for Ubuntu)
>        sudo chmod a+x /usr/sbin/pppd
> or under Ubuntu related Linuxes
>        sudo chmod a+x /usr/sbin/pppd
>
> Checking settings of:   /etc/ppp/options
> asyncmap 0
> noauth
> crtscts
> lock
> hide-password
> modem
> proxyarp
> lcp-echo-interval 30
> lcp-echo-failure 4
> noipx
>
> In case of a message like:
>   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
> see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)
>
> Read Modem/YourSystem.txt concerning other COMM channels: eth0
> Which can interfere with Browser naviagation.
>
>  Don't worry about the following, it is for the experts
>  should trouble shooting be necessary.
> ==========================================================
>
>  Checking for modem support lines:
>  --------------------------------------
>     /device/modem symbolic link:
> slmodemd created symbolic link /dev/ttySL0:
>     Within /etc/udev/ files:
>
>     Within /etc/modprobe.conf files:
> /etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
> /etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
> /etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
> /etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
> /etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
>     Within any ancient /etc/devfs files:
>
>     Within ancient kernel 2.4.n /etc/module.conf files:
>
> --------- end modem support lines --------
>
>
>



===============================================

i download : SLMODEMD.gcc4.2.tar.gz

./configure not worked with some problems!

but I used : sudo slmodemd -c Iran --alsa hw:0,6
the resolt is : bad country 'Iran'

Iused this one : sudo slmodemd -c India --alsa hw:0,6
and the resolt is :/dev/ttySL0 --> /dev/pts/2

but i cant find anything like ttySL0 in /dev and kppp cant worke
:(


Im too sad
help me please

---

### Post by mahmoos.sajjadi on 2008-05-28
Laptop : ASUS F3SV
Modem : Motorola SM56
OS : Linux Kubuntu Hardy i386


Please help me about my Modem!

tanx alot

---

### Post by mahmoos.sajjadi on 2008-05-28
:mad:
hey 
where are you ?
what can i do without my modem?
i'll back to Windows if nobady want to help me! and i'm so sad

---

### Post by sTpny on 2008-07-22
dont go just because you got an unsupported modem. Linux can't support some things that have proprietary licenses, and many companies don't release any information about their hardware at all, or only peices of it, (nvidia) to the open source community. This is not the fault of the community, it is the manufacturers trying to force you to a commercial platform, so that they can make more money off of you. I suggest you get a new modem. Buy used, and a few years old. You'll get it cheap because it's old and used, and modems have an excellent lifespan, and they haven't really changed much in years. Older hardware, and not a winmodem, is most likely to be recognized and properly configured by the system.  As I understand it, most modems do work now, but it seems like not this one.. I just put one into my machine.. it doesn't seem to work either, but lspci finds it and knows what it is, so I think it maybe is working, but just a configuration setting is off somewhere. If I can make mine work, I'll post you a link to how.. ok. And stick around.. things only get better... 

PS.. dual boot if you need your modem.. till its fixed or replaced.

---

