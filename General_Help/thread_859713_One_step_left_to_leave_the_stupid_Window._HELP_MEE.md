---
title: "One step left to leave the stupid Window. HELP MEEEEE"
date: 2008-07-14
forum: General Help
---

### Post by rakan_dr on 2008-07-14
Hi guys, 
please i did everything to leave that stupid OS Windows, i found all the alternatives that i need on Ubuntu and only one thing still that will let me remove windows at ALL, which is my modem.

Guys i have only Dialup connection, so i have to install my Dialup modem, otherwise i can't still using Ubuntu :(
I have Motorola SM56 speakerphone modem. 
When i wrote this in the terminal i got these info about my modem:

01:01.0 Communication controller: Motorola SM56 PCI Modem

	Subsystem: CIS Technology Inc SM56 PCI Speakerphone Modem

	Flags: bus master, medium devsel, latency 64, IRQ 10

	Memory at effffc00 (32-bit, prefetchable) [size=256]

	Capabilities: <access denied>

so guys plz tell me, Does Ubuntu recognize the modem or not???

I looked in [http://www.linmodems.org/](http://www.linmodems.org/) but i found nothing!

Please guys help me in this, i really want to leave Windows.
I'm new in Ubuntu, so make it easy for me plz :)
You're the only hope i have now.
Thnx

---

### Post by tramir on 2008-07-14
Check [this howto]("http://ubuntuforums.org/showthread.php?p=2756636"), it seems to be what you're looking for.

PS: the howto somehow assumes you'd still have a working internet connection. What you might want to do is download (from windows) the deb packages you need from ubuntu's website and then install them manually. For example, you can find sl-modem-daemon packages on [this page]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=sl-modem-daemon").

---

### Post by iaculallad on 2008-07-14
Try to visit this [Ubuntu Community Page]("https://help.ubuntu.com/community/DialupModemHowto") on how you can configure your Dial-Up connection.

---

### Post by jmore9 on 2008-07-14
I am using a us robotics external serial modem i got a thrift store for $2.00 and ubuntu sees it on install.  On my other machine i have a winmodem and i have some drivers for it.

Now what kind of modem is it ?  PCI , ISA , or Serial port ?

Have to start somewhere.

I also use pppconfig to setup my modem.  The only thing i have to do is to set the modem to tty0 instead of tty1 that pppconfig wamts to.

---

### Post by Taxman415a on 2008-07-14
> **tramir said:**
> 

PS: the howto somehow assumes you'd still have a working internet connection. What you might want to do is download (from windows) the deb packages you need from ubuntu's website and then install them manually. 

A good way to do this is to open synaptic and select the packages you want to install (linux-headers-generic and build-essential in this case, check for others) and after marking them for install, go to file --> generate download script. That script will give you download locations for all of the files and more importantly all the dependencies you need. Just copy that file to your windows box and copy and paste the urls into a browser to download all the files, then copy them back over to install them.

Also you really do need to run the scanmodem tool from linmodems.org since apparently some of the Motorola SM56 used different chips, etc. For detailed help on using the output of that file, the linmodem people would be better if it's not exactly the same as the guide tramir pointed you to.

---

### Post by rakan_dr on 2008-07-15
[COLOR="Red"]hi, guys i can't send any email to [email]discuss@linmodems.org[/email], i get a failur email back! This is what i get (This includes the info about my modem i hope u help me with it):[/COLOR]

Hi. This is the qmail-send program at ns0.crynwr.com.
I'm afraid I wasn't able to deliver your message to the following addresses.
This is a permanent error; I've given up. Sorry it didn't work out.

<discuss@linmodems.org>:
ezmlm-reject: fatal: Sorry, I don't accept messages of MIME Content-Type 'multipart/alternative' (#5.2.3)

--- Below this line is a copy of the message.

Return-Path: <xubuntu@ymail.com>
Received: (qmail 12881 invoked from network); 15 Jul 2008 10:41:14 -0000
Received: from n5a.bullet.mail.ac4.yahoo.com (76.13.13.68)
  by pdam.crynwr.com with SMTP; 15 Jul 2008 10:41:14 -0000
Received: from [76.13.13.26] by n5.bullet.mail.ac4.yahoo.com with NNFMP; 15 Jul 2008 10:38:59 -0000
Received: from [76.13.10.169] by t3.bullet.mail.ac4.yahoo.com with NNFMP; 15 Jul 2008 10:38:59 -0000
Received: from [127.0.0.1] by omp110.mail.ac4.yahoo.com with NNFMP; 15 Jul 2008 10:38:59 -0000
X-Yahoo-Newman-Property: ymail-3
X-Yahoo-Newman-Id: [email]605886.66903.bm@omp110.mail.ac4.yahoo.com[/email]
Received: (qmail 14372 invoked by uid 60001); 15 Jul 2008 10:38:59 -0000
DomainKey-Signature: a=rsa-sha1; q=dns; c=nofws;
  s=s1024; d=ymail.com;
  h=Received:X-Mailer:Date:From:Subject:To:MIME-Version:Content-Type:Message-ID;
  b=j/131DoNpIj2YqOpWHtN9/xHlL+zN+wGNuh/B3LZwilEK9Y/afcwyrYng+ogB3wyzoU0Q3QzBBAv446PFErjiXgo1Z2z0t22wKGAxWeJ1rF3MU90EFWFpm6FZ8VXhHNxx93bFVcDeIbRpN5gY2BglfLGnvyhtZOxwlcH18nIXcM=;
Received: from [78.110.96.5] by web59802.mail.ac4.yahoo.com via HTTP; Tue, 15 Jul 2008 03:38:59 PDT
X-Mailer: YahooMailRC/1042.40 YahooMailWebService/0.7.199
Date: Tue, 15 Jul 2008 03:38:59 -0700 (PDT)
From: Rocky Rock <xubuntu@ymail.com>
Subject: rockyrock, UAE
To: [email]Discuss@Linmodems.org[/email]
MIME-Version: 1.0
Content-Type: multipart/alternative; boundary="0-1007211234-1216118339=:13690"
Message-ID: <412225.13690.qm@web59802.mail.ac4.yahoo.com>

--0-1007211234-1216118339=:13690
Content-Type: text/plain; charset=us-ascii

Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
as HTML can contain viruses. Use as the email Subject Line:
          YourName, YourCountry  kernel 2.6.24-16-generic
With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
YourCountry will enable Country specific guidance. Linux experts in YourCountry
can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org)
--------------------------  System information ----------------------------
CPU=i686, 
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
scanModem update of:  2008_07_12

There are no blacklisted modem drivers in /etc/modprobe*  files
Attached USB devices are:
ID 3538:0042 Power Quotient International Co., Ltd Cool Drive U339 Flash Disk
ID 05e3:0760 Genesys Logic, Inc. USB 2.0 Card Reader/Writer
ID 03f0:5511 Hewlett-Packard
ID 09da:000a A4 Tech Co., Ltd

USB modems not recognized

For candidate card in slot 01:01.0, firmware information and bootup diagnostics are:
PCI slot    PCI ID        SubsystemID    Name
----------    ---------    ---------    --------------
01:01.0    11c1:0620    11c1:0620    Communication controller: Agere Systems Unknown device 0620

Modem interrupt assignment and sharing:
--- Bootup diagnostics for card in PCI slot 01:01.0 ----

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
PCI slot    PCI ID        SubsystemID    Name
----------    ---------    ---------    --------------
00:1b.0    8086:27d8    1043:8249    Audio device: Intel Corporation 82801G

Modem interrupt assignment and sharing:
20:      1129          0  IO-APIC-fasteoi  uhci_hcd:usb4, HDA Intel
--- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[  37.406156] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 20
[  37.406183] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics =====
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

PCI slot 00:1b.0 has a High Definition Audio Card
The drivers are in the kernel modules tree at:
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko

The ALSA verion is 1.0.15
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-02: ALC883 Analog : ALC883 Analog : capture 1
00-01: ALC883 Digital : ALC883 Digital : playback 1 : capture 1
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdfef8000 irq 20
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 01:01.0:
    Modem chipset  detected on
NAME="Communication controller: Agere Systems Unknown device 0620"
CLASS=0780
PCIDEV=11c1:0620
SUBSYS=11c1:0620
IRQ=10
IDENT=Agere.SV2P

For candidate modem in:  01:01.0
  0780 Communication controller: Agere Systems Unknown device 0620
      Primary device ID:  11c1:0620
Support type needed or chipset:    Agere.SV2P


----------------end Softmodem section --------------

Writing DOCs/Intel.txt

Vendor 11c1 is Lucent Technologies with modem technology now under LSI Inc.
Their Linux  code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its
continued maintenance is only initiated at the request of a major chipset buyer,
or comparable sponsor. Several different  modem chipset types  are produced:
with varying support under Linux.
Device ID  Support        Name          Comment
---------  -------------  -----------    -----------------------------
0480      serial drivers Venus          controller chipset 1673JV7
0440-045d  martian        Mars/Apollo    DSP (digital signal processing) chipsets
0462      none          56K.V90/ADSL Wildwire
048d none                  SV2P            soft modem
048(c or f) AGRSM        SV2P            soft modem
0600      none          soft modem, very few in the field.
0620      AGRSM          Pinball  soft modem, in some HP desktop PCs
011c11040  AGRSM_RedFlag  Softmodem on some High Definition Audio cards, support only for Red Flag kernel 2.6.21-20
062(1-3)  none          SV92PP,Pinball  soft modem, in some HP desktop PCs

martian - At [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/)
AGRSM - At [http://linmodems.technion.ac.il/packages/ltmodem/sv92/](http://linmodems.technion.ac.il/packages/ltmodem/sv92/) , the agrsm-20080203.tar.gz
AGRSM_RedFlag at  At [http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)
The  suse-10-2a.tar.gz has newer Agere/LSI code, but there are compiling problems with newer kernels/

From [http://linmodems.technion.ac.il/packages/ltmodem/sv92/](http://linmodems.technion.ac.il/packages/ltmodem/sv92/) download  agrsm-20080203.tar.gz
The  suse-10-2a.tar.gz thereat has newer Agere/LSI code,
but there are compiling problems with newer kernels
Read DOCs/Agrsm.txt

-------------- end Agere Systems section -------------------


Predictive diagnostics for card in bus 00:1b.0:
    Modem chipset not detected on
NAME="Audio device: Intel Corporation 82801G "
CLASS=0403
PCIDEV=8086:27d8
SUBSYS=1043:8249
IRQ=20
HDA=8086:27d8
SOFT=8086:27d8.HDA


High Definition Audio (HDA) cards MAY host a modem chip in their Subsystem,
and many are supported by the ALSA audio+modem driver snd-hda-intel
A modem was not detected on HDA card 8086:27d8.
If another modem card is present, then most likely 8086:27d8 does not host a modem.
If another modem card has not been detected, then possibilities are:
    1) A Conexant modem chip is present on 8086:27d8, as Conexant chips
are frequently not detectable by ALSA diagnostics
    2) The modem may be of the older non-PCI Controller Chipset (hardware) type.
Try detection with Root permission:
    sudo wvdialconf  /etc/wvdial.conf

For candidate modem in:  00:1b.0
  0403 Audio device: Intel Corporation 82801G
      Primary device ID:  8086:27d8
    Subsystem PCI_id  1043:8249
    Softmodem codec or chipset from diagnostics:
                              from    Archives:
                       
     

Support type needed or chipset:   

Support can likely be achieved through two mutually exclusive alternatives:
1) The hsfmodem software for Conexant chipset modems: Read DOCs/Conexant.txt
The following ALSA alternative CANNOT work with Conexant modems.

2) An ALSA modem driver plus slmodemd.  Read DOCs/Smartlink.txt for details, and
to test get the package SLMODEMD.gcc4.2.tar.gz from: 
    [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

----------------end Softmodem section --------------
Writing DOCs/Smartlink.txt
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
For martian_modem, additional required packages are n. The also required headers of package libc6 are commonly installed by default.
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
    -rwsr-xr-- 1 root dip 269256 2007-10-04 22:57 /usr/sbin/pppd

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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 eth0:avahi
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


     
--0-1007211234-1216118339=:13690
Content-Type: text/html; charset=us-ascii

<html><head><style type="text/css"><!-- DIV {margin:0px;} --></style></head><body><div style="font-family:times new roman, new york, times, serif;font-size:12pt"><div>&nbsp;Only plain text email is forwarded by the&nbsp; [email]Discuss@Linmodems.org[/email] List Server,<br>&nbsp;as HTML can contain viruses. Use as the email Subject Line:<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; YourName, YourCountry&nbsp; kernel 2.6.24-16-generic <br>&nbsp;With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.<br>&nbsp;YourCountry will enable Country specific guidance. Linux experts in YourCountry <br>&nbsp;can be found through: http://www.linux.org/groups/index.html.<br>They will know your Country's modem code, which may be essential for dialup service.<br>Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.<br>&nbsp;So in a day, also check the Archived responses at
[http://www.linmodems.org](http://www.linmodems.org) <br>--------------------------&nbsp; System information ----------------------------<br>CPU=i686,&nbsp; <br>Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008<br>&nbsp;scanModem update of:&nbsp; 2008_07_12<br><br>&nbsp;There are no blacklisted modem drivers in /etc/modprobe*&nbsp; files <br>Attached USB devices are:<br>&nbsp;ID 3538:0042 Power Quotient International Co., Ltd Cool Drive U339 Flash Disk<br>&nbsp;ID 05e3:0760 Genesys Logic, Inc. USB 2.0 Card Reader/Writer<br>&nbsp;ID 03f0:5511 Hewlett-Packard <br>&nbsp;ID 09da:000a A4 Tech Co., Ltd <br><br>USB modems not recognized<br><br>For candidate card in slot 01:01.0, firmware information and bootup diagnostics are:<br>&nbsp;PCI slot&nbsp;&nbsp;&nbsp; PCI ID&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; SubsystemID&nbsp;&nbsp;&nbsp; Name<br>&nbsp;----------&nbsp;&nbsp;&nbsp; ---------&nbsp;&nbsp;&nbsp;
---------&nbsp;&nbsp;&nbsp; --------------<br>&nbsp;01:01.0&nbsp;&nbsp;&nbsp; 11c1:0620&nbsp;&nbsp;&nbsp; 11c1:0620&nbsp;&nbsp;&nbsp; Communication controller: Agere Systems Unknown device 0620<br><br>&nbsp;Modem interrupt assignment and sharing: <br>&nbsp;--- Bootup diagnostics for card in PCI slot 01:01.0 ----<br><br>For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:<br>&nbsp;PCI slot&nbsp;&nbsp;&nbsp; PCI ID&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; SubsystemID&nbsp;&nbsp;&nbsp; Name<br>&nbsp;----------&nbsp;&nbsp;&nbsp; ---------&nbsp;&nbsp;&nbsp; ---------&nbsp;&nbsp;&nbsp; --------------<br>&nbsp;00:1b.0&nbsp;&nbsp;&nbsp; 8086:27d8&nbsp;&nbsp;&nbsp; 1043:8249&nbsp;&nbsp;&nbsp; Audio device: Intel Corporation 82801G <br><br>&nbsp;Modem interrupt assignment and sharing: <br>&nbsp;20:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1129&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp; IO-APIC-fasteoi&nbsp;&nbsp;
uhci_hcd:usb4, HDA Intel<br>&nbsp;--- Bootup diagnostics for card in PCI slot 00:1b.0 ----<br>[&nbsp;&nbsp; 37.406156] ACPI: PCI Interrupt 0000:00:1b.0[A] -&gt; GSI 19 (level, low) -&gt; IRQ 20<br>[&nbsp;&nbsp; 37.406183] PCI: Setting latency timer of device 0000:00:1b.0 to 64<br><br><br>===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== <br>The ALSA packages provide audio support and also drivers for some modems.<br>ALSA diagnostics are written during bootup to /proc/asound/ folders.<br><br>&nbsp;PCI slot 00:1b.0 has a High Definition Audio Card<br>&nbsp;The drivers are in the kernel modules tree at:<br>&nbsp;/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko<br><br>The ALSA verion is 1.0.15<br>The modem cards detected by "aplay -l"&nbsp; are: None<br><br><br>The /proc/asound/pcm file reports:<br>-----------------------<br>00-02: ALC883 Analog : ALC883 Analog : capture 1<br>00-01: ALC883 Digital : ALC883
Digital : playback 1 : capture 1<br>00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 1<br><br>about /proc/asound/cards:<br>------------------------<br>&nbsp;0 [Intel&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]: HDA-Intel - HDA Intel<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; HDA Intel at 0xdfef8000 irq 20<br>=== Finished firmware and bootup diagnostics, next deducing cogent software. ===<br><br>Predictive diagnostics for card in bus 01:01.0:<br>&nbsp;&nbsp;&nbsp; Modem chipset&nbsp; detected on<br>NAME="Communication controller: Agere Systems Unknown device 0620"<br>CLASS=0780<br>PCIDEV=11c1:0620<br>SUBSYS=11c1:0620<br>IRQ=10<br>IDENT=Agere.SV2P<br><br>&nbsp;For candidate modem in:&nbsp; 01:01.0<br>&nbsp;&nbsp; 0780 Communication controller: Agere Systems Unknown device 0620<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Primary device ID:&nbsp;
11c1:0620<br>&nbsp;Support type needed or chipset:&nbsp;&nbsp;&nbsp; Agere.SV2P<br>&nbsp;<br><br>----------------end Softmodem section --------------<br><br>Writing DOCs/Intel.txt<br><br>&nbsp;Vendor 11c1 is Lucent Technologies with modem technology now under LSI Inc. <br>Their Linux&nbsp; code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its <br>&nbsp;continued maintenance is only initiated at the request of a major chipset buyer,<br>&nbsp;or comparable sponsor. Several different&nbsp; modem chipset types&nbsp; are produced: <br>&nbsp;with varying support under Linux.<br>&nbsp;Device ID&nbsp; Support&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Name&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Comment<br>&nbsp;---------&nbsp; -------------&nbsp; -----------&nbsp;&nbsp;&nbsp; -----------------------------<br>&nbsp;0480&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; serial drivers
Venus&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; controller chipset 1673JV7<br>&nbsp;0440-045d&nbsp; martian&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Mars/Apollo&nbsp;&nbsp;&nbsp;&nbsp; DSP (digital signal processing) chipsets<br>&nbsp;0462&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; none&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 56K.V90/ADSL Wildwire <br>&nbsp;048d none&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp; SV2P&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; soft modem <br>&nbsp;048(c or f) AGRSM&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SV2P&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; soft modem<br>&nbsp;0600&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; none&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; soft modem, very few in the field.<br>&nbsp;0620&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
AGRSM&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Pinball&nbsp; soft modem, in some HP desktop PCs<br>&nbsp;011c11040&nbsp; AGRSM_RedFlag&nbsp; Softmodem on some High Definition Audio cards, support only for Red Flag kernel 2.6.21-20<br>&nbsp;062(1-3)&nbsp;&nbsp; none&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SV92PP,Pinball&nbsp; soft modem, in some HP desktop PCs<br><br>martian - At http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/<br>AGRSM - At [http://linmodems.technion.ac.il/packages/ltmodem/sv92/](http://linmodems.technion.ac.il/packages/ltmodem/sv92/) , the agrsm-20080203.tar.gz<br>AGRSM_RedFlag at&nbsp; At http://linmodems.technion.ac.il/packages/ltmodem/11c11040/<br>The&nbsp; suse-10-2a.tar.gz has newer Agere/LSI code, but there are compiling problems with newer kernels/<br><br>From [http://linmodems.technion.ac.il/packages/ltmodem/sv92/](http://linmodems.technion.ac.il/packages/ltmodem/sv92/) download&nbsp; agrsm-20080203.tar.gz<br>The&nbsp; suse-10-2a.tar.gz thereat has newer Agere/LSI code, <br>but there are
compiling problems with newer kernels<br>Read DOCs/Agrsm.txt<br><br>-------------- end Agere Systems section -------------------<br><br><br>Predictive diagnostics for card in bus 00:1b.0:<br>&nbsp;&nbsp;&nbsp; Modem chipset not detected on<br>NAME="Audio device: Intel Corporation 82801G "<br>CLASS=0403<br>PCIDEV=8086:27d8<br>SUBSYS=1043:8249<br>IRQ=20<br>HDA=8086:27d8<br>SOFT=8086:27d8.HDA<br><br><br>&nbsp;High Definition Audio (HDA) cards MAY host a modem chip in their Subsystem, <br>&nbsp;and many are supported by the ALSA audio+modem driver snd-hda-intel<br>&nbsp;A modem was not detected on HDA card 8086:27d8.<br>&nbsp;If another modem card is present, then most likely 8086:27d8 does not host a modem.<br>&nbsp;If another modem card has not been detected, then possibilities are:<br>&nbsp;&nbsp;&nbsp; 1) A Conexant modem chip is present on 8086:27d8, as Conexant chips<br>&nbsp;are frequently not detectable by ALSA diagnostics<br>&nbsp;&nbsp;&nbsp; 2)
The modem may be of the older non-PCI Controller Chipset (hardware) type.<br>Try detection with Root permission:<br>&nbsp;&nbsp;&nbsp; sudo wvdialconf&nbsp; /etc/wvdial.conf<br><br>&nbsp;For candidate modem in:&nbsp; 00:1b.0<br>&nbsp;&nbsp; 0403 Audio device: Intel Corporation 82801G <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Primary device ID:&nbsp; 8086:27d8<br>&nbsp;&nbsp;&nbsp; Subsystem PCI_id&nbsp; 1043:8249 <br>&nbsp;&nbsp;&nbsp; Softmodem codec or chipset from diagnostics: <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; from&nbsp;&nbsp;&nbsp; Archives: <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <br><br>Support type needed or chipset:&nbsp;&nbsp;&nbsp; <br><br>Support can likely be
achieved through two mutually exclusive alternatives:<br>1) The hsfmodem software for Conexant chipset modems: Read DOCs/Conexant.txt<br>The following ALSA alternative CANNOT work with Conexant modems.<br><br>2) An ALSA modem driver plus slmodemd.&nbsp; Read DOCs/Smartlink.txt for details, and<br>to test get the package SLMODEMD.gcc4.2.tar.gz from:&nbsp; <br>&nbsp;&nbsp;&nbsp; http://linmodems.technion.ac.il/packages/smartlink/<br><br>----------------end Softmodem section --------------<br>Writing DOCs/Smartlink.txt<br>============ end Smartlink section =====================<br><br>&nbsp;Completed candidate modem analyses.<br><br>&nbsp;The base of the UDEV device file system is: /dev/.udev<br><br>&nbsp;Versions adequately match for the compiler installed: 4.2.3<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; and the compiler used in kernel assembly: 4.2.3<br><br><br>&nbsp;<br>&nbsp;Minimal compiling resources appear
complete:<br>&nbsp;&nbsp; make utility - /usr/bin/make<br>&nbsp;&nbsp; Compiler version 4.2<br>&nbsp;&nbsp; linuc_headers base folder /lib/modules/2.6.24-16-generic/build<br><br>&nbsp;However some compilations and executable functions may need additional files,<br>&nbsp;in the FileNames.h (so called kernel "h"eaders) collection installed in&nbsp; /usr/include/ .<br>&nbsp;For martian_modem, additional required packages are n. The also required headers of package libc6 are commonly installed by default. <br>&nbsp;Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.<br>&nbsp;In not included on your install CD, search for them at http://packages.ubuntu.com<br>&nbsp;or comparable Repository for other Linux distros.<br>&nbsp;When compiling ALSA drivers, the utility "patch" will also be needed.<br><br><br><br><br>If a driver compilation fails, with message including some lack of some FileName.h
(stdio.h for example), then<br>Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev<br>and any of its dependents, under Ubuntu linux-libc-dev<br><br>If an alternate ethernet connection is available,<br>$&nbsp; apt-get update<br>$&nbsp; apt-get -s install linux-kernel-devel<br>will install needed packages.<br>For Debian/Ubuntu related distributions, run the following command to display the needed package list:<br><br>Otherwise packages have to be found through http://packages.ubuntu.com<br>Once downloaded and transferred into a Linux partition,<br>they can be installed alltogether with:<br>$ sudo dpkg -i *.deb<br><br><br>Checking pppd properties:<br>&nbsp;&nbsp;&nbsp; -rwsr-xr-- 1 root dip 269256 2007-10-04 22:57 /usr/sbin/pppd<br><br>In case of an "error 17" "serial loopback" problem, see:<br>&nbsp;&nbsp;&nbsp; http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html<br><br>To
enable dialout without Root permission do:<br>&nbsp;&nbsp;&nbsp; $ su - root&nbsp; (not for Ubuntu)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; sudo chmod a+x /usr/sbin/pppd<br>or under Ubuntu related Linuxes<br>&nbsp;&nbsp;&nbsp; sudo chmod a+x /usr/sbin/pppd<br><br>Checking settings of:&nbsp;&nbsp;&nbsp; /etc/ppp/options<br>asyncmap 0<br>noauth<br>crtscts<br>lock<br>hide-password<br>modem<br>proxyarp<br>lcp-echo-interval 30<br>lcp-echo-failure 4<br>noipx<br><br>In case of a message like:<br>&nbsp;&nbsp; Warning: Could not modify /etc/ppp/pap-secrets: Permission denied<br>see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html<br><br>Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 eth0:avahi<br>Which can interfere with Browser naviagation.<br><br>&nbsp;Don't worry about the following, it is for experts should trouble shooting be
necessary.<br>==========================================================<br><br>&nbsp;Checking for modem support lines:<br>&nbsp;--------------------------------------<br>&nbsp;&nbsp;&nbsp;&nbsp; /device/modem symbolic link:&nbsp;&nbsp; <br>slmodemd created symbolic link /dev/ttySL0:&nbsp; <br>&nbsp;&nbsp;&nbsp;&nbsp; Within /etc/udev/ files:<br><br>&nbsp;&nbsp;&nbsp;&nbsp; Within /etc/modprobe.conf files:<br>/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2<br>/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2<br>/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers<br>/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem<br>/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem<br>&nbsp;&nbsp;&nbsp;&nbsp; Within any ancient /etc/devfs files:<br><br>&nbsp;&nbsp;&nbsp;&nbsp; Within ancient kernel 2.4.n /etc/module.conf files:<br><br>--------- end modem support lines
--------<br><br><br></div></div><br>



      </body></html>
--0-1007211234-1216118339=:13690--

---

### Post by Taxman415a on 2008-07-15
It says in that error response email why it failed - "Only plain text email is forwarded by the [email]Discuss@Linmodems.org[/email] List Server, as HTML can contain viruses."  You sent it from a yahoo address which defaults to html email. You have to go into your yahoo mail preferences and choose one of the options to get it to default to text only.

Also your message above is mangled in parts, it would probably be better to edit it and replace it with a clean copy of the scanmodem results.

---

### Post by rakan_dr on 2008-07-15
thanks man

---

