---
title: "snd-hda-intel softmodem (si3054) and slmodemd"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by maximk on 2007-04-21
Trying to make internal modem of my toshiba L30 work... without success yet.

According to 'scanmodem' results my laptop's modem is one of HDA soundcard modems.

So, I install slmodemd, configure SLMODEMD_DEVICE to hw:0,6 (other values were tested, but errors on earlier stages of slmodemd execution occurs) and started sl-modem-daemon .

Ok, now I see /dev/ttySL0 device (actually symbolic link) and it is usable via "minicom".
Next step is to configure wvdial and execute it... but without success...

```

...
--> Modem initialized.
--> Sending: ATDTXXX
--> Waiting for carrier.
ATDTXXX
NO CARRIER
ERROR
...

```

If I run slmodemd manually from terminal I see following error:
```

error: period size 48 is not supported by playback (64).

```

And here I got stuck - googling for such error message gives no results.

---

### Post by exidez on 2007-04-26
i got this error too

i have recently install slmodem and all went good but as soon as i dail i get the error
period size 48 is not supported by playback (64)

---

### Post by maximk on 2007-04-26
It seems like a new modem chip and it is not currently supported, though recognized by driver. See my post in linmodems ML below:

[http://linmodems.org/cgi-bin/ezmlm-cgi?1:mss:26547:200704](http://linmodems.org/cgi-bin/ezmlm-cgi?1:mss:26547:200704)

---

### Post by DraxNS on 2007-05-27
Same exact error on Feisty.

Modem is some HDA, detected by scanmodem as Smartlink. I have downloaded slmodemd package first, tested it and failed with same errors.
Afterwards, I have tried sl-modemd (or whatever) package from repo... same thing.

Worst of all... it was working on Edgy!! And it was on 64bit version... so I was confident that it will work in Feisty.

I am going to try and mess a bit with Alsa...  wish me luck..

update: no luck with alsa yet... added new config in /etc/modprobe.d called alsa and sound... still NO CARRIER with vwdial, pon, and kppp.

I have downloaded latest slmodem script, and tried to install and it returned me an error about version... will paste it once I get back home.

---

### Post by DraxNS on 2007-05-30
here is that error, but do mind that ungrab-winmodem and slamr ARE in directory from where install started, per README/INSTALL texts


sudo ./setup
driver=slamr
When asked about your country, Enter:
        USA

Installing the Debian packages supporting autoloading
Selecting previously deselected package sl-modem-daemon.
(Reading database ... 112888 files and directories currently installed.)
Unpacking sl-modem-daemon (from sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb) ...
Setting up sl-modem-daemon (2.9.10+2.9.9d+e-pre2-5build1) ...
FATAL: Module ungrab_winmodem not found.
FATAL: Module slamr not found.
Starting SmartLink Modem driver for: auto.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.


Copying over newer files
cp: cannot stat `sl-modem-daemon.modutils': No such file or directory
Making folder /lib/modules/2.6.20-15-386/extra
Copying drivers to /lib/modules/2.6.20-15-386/extra
Checking driver install
et131x.ko  slamr.ko  slusb.ko  ungrab-winmodem.ko
Finished installs.
Informing the System

Starting function tests, loading drivers:
FATAL: Error inserting ungrab_winmodem (/lib/modules/2.6.20-15-386/extra/ungrab-winmodem.ko): Invalid module format
FATAL: Error inserting ungrab_winmodem (/lib/modules/2.6.20-15-386/extra/ungrab-winmodem.ko): Invalid module format
FATAL: Error inserting slamr (/lib/modules/2.6.20-15-386/extra/slamr.ko): Invalid module format
Running diagnostic:

[ 1133.328000] slamr: disagrees about version of symbol struct_module

ports should be created by:
slmodemd -c USA /dev/slamr0
error: mdm setup: cannot open dev `/dev/slamr0': No such device or address
error: cannot setup device `/dev/slamr0'
Checking for success
Port creation with slmodemd failed.
Read the Slamr.txt record, other 1st_Read.txt CountryList.txt wvdial.txt files and the sample wvdial.conf.

---

### Post by DraxNS on 2007-05-31
Now I am waaay to upset!!!! I have lost whole day fiddling with dozen tutorials, source files, packages. what not.. compiled.. recompiled.. with NO result!!

I just can't get my modem to run under Feisty!!

Here is scanModem output
```
./scanModem

 From http://linmodems.technion.ac.il , get a recent update of scanModem,
 if this copy was not there obtained. There are weekly updates.
 Updated on: 2007_May_11

Identifying PCI bus slots with candidate modems.
 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

Analysing card in PCI bus 00:14.2, writing to scanout.00:14.2
        Modem with PCI ID 1002:437b is in the software modem category.
grep: /proc/sound/cards: No such file or directory
Checking for match with Archived softmodem information.
IDENT=slmodemd
Using scanout.00:14.2 data, and writing guidance to ModemData.txt
Writing Smartlink.txt

```

Modem data:
```

 Only plain text email is forwarded by the  DISCUSS@linmodems.org List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-15-386 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org .
 Local Linux experts can be found through: http://www.linux.org/groups/index.html
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-15-386 (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Sun Apr 15 07:34:00 UTC 2007
 scanModem update of:  2007_May_11
The modem symbolic link is /dev/modem -> ttySL0

ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:14.2	1002:437b	1462:0369	Audio device: ATI Technologies Inc SB450 HDA Audio 

 Modem interrupt assignment and sharing: 
 17:     215748   IO-APIC-fasteoi   HDA Intel, ra0

 --- Bootup diagnositcs for card in PCI slot 00:14.2 ----
[   37.429862] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

1002:437b is a High Definition Audio card, possibly hosting a soft modem.
 For candidate modem in PCI bus:  00:14.2
   Class 0403: 1002:437b Audio device: ATI Technologies Inc SB450 HDA Audio
      Primary PCI_id  1002:437b
    Subsystem PCI_id  1462:0369 
    Softmodem codec or Vendor from diagnostics: 
                              from    Archives: 11c1, an AgereSystems type.
                        

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	slmodemd

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from http://linmodems.technion.ac.il/packages/smartlink/ 
 the package SLMODEMD-1.0.13.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD-1.0.13.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6 
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

 Already loaded into the kernel is snd-hda-intel and audio drivers it depends on,
 displayed by:	lsmod | grep snd_hda_intel
Module                  Size  Used by
-------------------------------------
snd_hda_intel          20504  1 
snd_hda_codec         204544  1 snd_hda_intel
snd_pcm                76680  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    51716  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          9992  2 snd_hda_intel,snd_pcm


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-02: ALC882 Analog : ALC882 Analog : capture 2
00-01: ALC882 Digital : ALC882 Digital : playback 1
00-00: ALC882 Analog : ALC882 Analog : playback 1 : capture 2

	/proc/asound/modules
-------------------------------
 0 snd_hda_intel
and from the command:
	aplay -l | grep -i modem
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]

----------------end Softmodem section --------------
The modem is supported by the Smartlink slamr driver
plus the slmodemd helper utility.  Read the
Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

Writing Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	 linux-headers-2.6.20-15-386
Compressed files at: /usr/src/fglrx.tar.bz2


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269224 2007-04-05 05:41 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html

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

Read Modem/YourSystem.txt concerning other COMM channels: eth0 ra0 vmnet1 vmnet8
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   lrwxrwxrwx 1 root root 6 2007-05-31 22:22 /dev/modem -> ttySL0
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

```

In the name of GOD... can anyone of this world help me set it up??



I have used precompiled slmodemd binary and that is only one ever worked, 'till NO CARRIER error, all other efforts did not even get there!

So to help you help me:
-1. tried precompiled slmodemd binary, it creates all that needs to be created, but all ppp tools return NO CARRIER even though I have entered both stupid mode and no carrier check in vwdial.conf
-2. then tried newest package from smartlink site, section ubuntu, and failed to  install it with errors no winmodem_unload and no slamd modules even that they are present in that directory from where install started
-3. then tried sl-modem-module with precompiled slmodemd ... no luck
-4. wasn't lazy so decided to compile ungrab_winmodem and slamd since I saw on some links that ungrab_winmodem source code has to be altered in one line... done that... it compiled... installed.. modprobed... sl-modem-module restarted... and nothing!! I have so much garbage in shell history now... so I just cant get those errors... but what I saw... is that that module from repo does not create /dev/ttySL0 so /dev/modem is broken and there is /dev/-slamd0
-5. now exausted... removed all... and tried some other precompiled slmodemd.. also get modem init.. modem query works.. and just NO CARRIER

here is uname:
```

uname -a
Linux kubuntu-lap 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux
```

I had to switch to i386 because one other thing was broken in Feisty ... and that is ra0 (rt61) wlan card, that DOES NOT WORK on SMP enabled kernel!

More I use Feisty, I find out that it is much worse than Edgy... total miss... 

Also I get a distinct feeling that this (these) issue is easily overlooked by developers since I saw just few replies on this issue.... I just cant believe that I am only one that has this issue, and I am not since google is full of questions, but no valid answer.


If there is someone who thinks that can help me... please let me know, I'll open new account on laptop.. will start sshd and let him/her get all info first hand. I am just exausted and way to frustrated to continue...

PLEASE HELP ME,  I am just out of ideas.

---

### Post by handaxe on 2007-05-31
Hi, 

Off my broadband so I just met this issue myself. Was working in Edgy so not a new chip issue.  In fact, my brief research points to an Alsa related bug ....

see [http://linmodems.technion.ac.il/bigarch/archive-seventh/msg01288.html](http://linmodems.technion.ac.il/bigarch/archive-seventh/msg01288.html)

I am continuing to probe this....

HA

---

### Post by DraxNS on 2007-06-01
will test this later on.... for sure

update: nope... downloading newest alsa and alsa-lib and recompiling it to that thread did not help.

I still get no carrier error, with precompiled slmodemd 1.0.13. That is newest one I could find.

Again... modem responds to query... just does not find carrier.


tried both with ./slmodemd --alsa -c SLOVENIA hw:0,6 and ./slmodemd --alsa -c SLOVENIA hw:0

all I see in konsole is:
```
error: period size 48 is not supported by playback (64).
```

Here is what wvdial says:
```

wvdial
--> WvDial: Internet dilaer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending ATZ
ATZ
OK
--> Sending AT+MS=34
AT+MS=34
OK
--> Modem initialized.
--> Sending: ATDT042112242
--> Waiting for carrier.
ATDT042112242
NO CARRIER
ERROR
--> No Carrier! Trying again.
--> Sending: ATDT042112242
--> Waiting for carrier.
ATDT042112242
NO CARRIER
ERROR
--> No Carrier! Trying again.
```

etc... until I stop wvdial

and wvdial.conf is like this:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+MS=34
Modem Type = Analog Modem
Baud = 57600
New PPPD = yes
Modem = /dev/ttySL0
ISDN = 0
Phone = 042110042
Password = my pass
Username = my username
Carrier Check = no
Stupid Mode = yes
```

---

### Post by mulvila on 2007-06-02
I was having this problem yeasterday with my lap-top when I tried to use the modem first time after shifting to Feisty. This morning I reinstalled sl-modem package from synaptic and now the modem worked well.

My /etc/default/sl-modem-daemon file is like this:
```

SLMODEMD_DEVICE=auto
SLMODEMD_COUNTRY=USA
FORCESTART=0

```
though, I live in Finland.

Hope this helps (reinstalling sl-modem package or changing the DEVICE to auto).

---

