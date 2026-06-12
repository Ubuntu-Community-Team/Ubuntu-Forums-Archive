---
title: "Is Someone willing to walk me through this?"
date: 2006-05-07
forum: Hardware &amp; Laptops
---

### Post by ttt06 on 2006-05-07
Hello gang.
I am a new user. Very new! I'm trying to get Ubuntu going on two different laptops. (Compaq Armada E500 & ThinkPad i-series 1200)
I have 5.04 & 5.10 CD's, but 5.10's don't want to boot.
The 5.04 CD's installed fine on both machines.
I am totally new to this and I just don't understand all the ling about getting my modems to work.

I put that scanModem thing on a usb stick and transferred it to the desktop.
I opened a terminal and did ./scanModem.
It made a modem folder with all kinds of stuff in it that I don't understand.

I wonder if some kind soul would take the time to walk me through the process, because I don't have a clue how to go about it & I don't want to install the wrong stuff & screw it up.

Thanks in advance for reading my first post.

---

### Post by Jussi Kukkonen on 2006-05-07
[QUOTE=ttt06]
I put that scanModem thing on a usb stick and transferred it to the desktop.
I opened a terminal and did ./scanModem.
It made a modem folder with all kinds of stuff in it that I don't understand.

I wonder if some kind soul would take the time to walk me through the process, because I don't have a clue how to go about it & I don't want to install the wrong stuff & screw it up.
[/QUOTE]

Never worked with winmodems myself, but I do know that if scanmodem works, it creates a *ModemData.txt* file in the modem-folder. You should probably paste the contents here.

---

### Post by ttt06 on 2006-05-07
Thanks for the reply,
UPDATE: I got 5.10 to install on Compaq ARmada, after 5.04 was already installed.

Below is the output from ModemData.txt, as run on Compaq with 5.10.


<begin paste>

 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_April_26
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386

 [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) has good general guidance.
 Be sure to read the Ethernet section of Modem/YourSystem.txt 
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
	Reading /proc/asound/pcm 
00-00: ESS Maestro : ESS Maestro : playback 4 : capture 1
 The potentially supporting drivers now loaded on this System are:
0 snd_es1968


 The kernel was assembled with compiler:  3.4.5
 with current System compiler GCC=4.0.2
-------------
 Found make utility.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-headers supporting compiling are resident: 

Modem candidates are at PCI_buses:  0000:00:09.1
    
Providing detail for device at  0000:00:09.1
  with vendor-ID:device-ID
	    ----:----
Class 0700: 11c1:0445   Serial controller: Lucent Microelectronics LT WinModem (prog-if 00 [8250])
  SubSystem 8086:2204  Intel Corp. PRO/100+ MiniPCI on Armada E500
	Flags: medium devsel, IRQ 11
 Checking for IRQ 11 sharing with modem.
      XT-PIC  uhci_hcd:usb1, yenta, yenta, ESS Maestro, eth0

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:0445 8086:2204 debian_version 2.6.12-9-386  3.4.5 4.0.2    i686
 == Checking PCI IDs through modem chip suppliers ==
	  
 The modem has a supported Lucent/Agere DSP (digital signal processing) Mars or Apollo DSP
 (digital signal processing) chipset with primary PCI_ID:  11c1:0445
 DSP=1

Support packages for 2.6.n kernels are at:
[http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/) with folders for
	debian/  containing some installers
	ubuntu/  containing some installers
The ltmodem-8.26b1.tar.gz  and ltmodem-8.31b1.tar.gz are driver compiling resources,
with the 8.31 having support for SMP (symmetric multi processor) motherboards.
These packages are more automated versions of the ltmodem-2.6-alk* packages
The ltmodem-2.6-Nalk.src.rpm packages can be used with rpm using Distros.
	   # rpmbuild --rebuild ltmodem-2.6-Nalk.src.rpm  
	   will deposit an installer at:
	        /usr/src/rpm/RPMS/i686/ltmodem-kv_2.6.12-9-386.rpm 	   Check with  
            # ls -l   /usr/src/rpm/RPMS/i686/ltmodem*
	    Then install with:
	    # rpm -i /usr/src/rpm/RPMS/i686/ltmodem-kv_2.6.12-9-386.rpm
	    or similar.

The martian.tar.gz represents a new developmental track, meeting emerging kernel requirements.
See for details:  [http://martian.barrelsoutofbond.org/](http://martian.barrelsoutofbond.org/)
[http://linmodems.technion.ac.il/archive-sixth/msg00142.html](http://linmodems.technion.ac.il/archive-sixth/msg00142.html)
AMD x86_64 competency is provided only bt the martian.

For 2.4.n kernels packages are at [http://ltmodem.heby.de/](http://ltmodem.heby.de/) or [http://phep2.technion.ac.il/linmodems/packages/ltmodem/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/)

 There are some installer packages and also resources for compiling drivers.
 ----------------------
 SuSE/Novell Linux and some other Distros provide compiled drivers +installers.
    Search package lists for ltmodem  
 For other Distros and 2.6.n kernels, see: 

 Packages for compiling drivers are:
 ResourceName                Use for kernel ranges
--------------------------------------------------------------------------------
ltmodem-8.26a.tar.gz         2.4.21 and earlier
ltmodem-8.30a3.tar.gz        2.4.21 and subsequent 2.4.2n kernels
	    which were assembled with a gcc-2.9 comiler
ltmodem-8.31a10.tar.gz     beginning with 2.4.21 and upto about 2.6.8  kernels
martian.tar.gz             2.6.n SMP (symmetic multiprocessor) support not verified.
ltmodem-8.31b1.tar.gz      2.6.n with    SMP support, for some* Systems
ltmodem-8.26b1tar.gz       2.6.n without SMP support
   * While SMP capacity should in principle be without ill effect on single processor systems,
the are some cases of ill effects on single processor systems.

Some additional 2.4.n installers are available from:
[http://dag.wieers.com/packages/kernel-module-ltmodem/](http://dag.wieers.com/packages/kernel-module-ltmodem/) for some other 2.4.n installers.


 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  [http://www.agere.com/client/modem_dsp.html](http://www.agere.com/client/modem_dsp.html). Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
   
 Lucent/Agere Mars/WinModem drivers from version 8.30 onwards have
 the necessary fix for SMP machines which includes machines with
 hyperthreading turned on (virtually acting as two CPUs).
 
 Call waiting specified by, +pcw=1, is not implmented in the ltmodem drivers.
Configuration with forcing is described in: [http://linmodems.technion.ac.il/archive-fifth/msg00055.html](http://linmodems.technion.ac.il/archive-fifth/msg00055.html)
 0x0445 -- Apollo 2 Global Board data/fax only : Modem/LAN combo board Apollo behind an Intel 82559


  The desired installer name is like:
========================================
ltmodem-2.6.12-9-386_8.nn_i386.deb
----------------------------------------
 ltmodem-kv-Kernel_FL-LTver--.CPU.rpm   explains the versioning.
 For your System
            Kernel_FL is 2.6.12-9-386 , the full kernel version displayed by: uname -r
                      LTver is 8.31b1, the release of the compiler kit
                               8.nn is the Agere core code designation.
       The proccesor type or CPU is:  i686      dispayed by:  uname -m
 used in compiling and assembling driver packages.

      
 A suitable installer is not available as of this 2006_April_26 update.
 Check in the section debian_version at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
   for a subsequent Installer submission.
 Older releases have been archived at:
   [http://linmodems.technion.ac.il/packages/ltmodem/archive/](http://linmodems.technion.ac.il/packages/ltmodem/archive/)
 Also there is a RPM search engine at:   [http://rpm.pbone.net](http://rpm.pbone.net)
 The closest match to your   i686=CPU   is recommended.
   The closest match to your   i686=CPU   is recommended.
   For example replacements in order of preference for an
     i686 would be i586, i486 and i386
 If not present use the  ltmodem-8.31b1.tar.gz compiler kit.

 The list of available Installers for debian_version as of this 2006_April_26
 is inserted into to Modem/YourSystem.txt
  ======= PCI_ID checking completed ====== 
 Update=2006_April_26

Analyzing information for PCMCIA device at PCI Bus 00:04.0
0000:00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
	Subsystem: Compaq Computer Corporation Armada E500
	Flags: bus master, medium devsel, latency 168, IRQ 11
GREPping for an inserted PCMCIA modem with filter:        ommunication

Analyzing information for PCMCIA device at PCI Bus 00:04.1
0000:00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
	Subsystem: Compaq Computer Corporation Armada E500
	Flags: bus master, medium devsel, latency 168, IRQ 11
GREPping for an inserted PCMCIA modem with filter:        ommunication
 If a PCMCIA modem is currently inserted and the sockets activated by
    /etc/init.d/pcmcia start
 then the PCMCIA bridge is NOT transparent.

 If the modem is known to have a Lucent digital signal processing chipset,
 then PCMCIA.tar.gz variant assembled by Joern Wustenfeld is necessary,
 rather than the standard ltmodem-8.31b1.tar.gz at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
drwxr-xr-x  2 root root 0 2006-05-07 14:50 /dev/.udevdb

There is an active UDEV file system, creating device nodes in volatile RAM.
For SmartLink modems using the slamr.ko or slusb.ko drivers an /etc/init.d/ script
will be necessary to create /dev/slamr0 or /dev/slusb0 ports, or manually by:
#  mknod -m 600 /dev/slamr0 c 242 0
#  mknod -m 600 /dev/slusb0 c 243 0
upon each bootup.

For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere DSP modems
   
 Checking for modem symbolic link support lines within /etc/udev/ files


Checking the /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted




deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse




A package kernel-kbuild-2.6-3 or later version must be installed to support compiling


    /usr/bin/gcc -> gcc-4.0
      
 The Major.Minor versions differ in the designated compiler 4.0.2 and the 3.4.5 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See [http://linmodems.technion.ac.il/archive-fifth/msg04252.html](http://linmodems.technion.ac.il/archive-fifth/msg04252.html) 
 
 A /dev/modem symbolic link is not set.

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe_mppc
-------------------------------------
 Resident PPP support modules are properly uncompressed .
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:D0:59:4B:93:CF  
          inet6 addr: fe80::2d0:59ff:fe4b:93cf/64 Scope:Link
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/YourSystem.txt
 ---- dmesg queries -------
[4294669.125000] ACPI: PCI Interrupt Link [C13F] (IRQs 11) *0, disabled.
[4294669.202000] audit: initializing netlink socket (disabled)
[4294704.939000] shpchp: acpi_shpchprm:\_SB_.C005 evaluate _BBN fail=0x5
[4294704.939000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294721.970000] ibm_acpi: ec object not found
[4294737.534000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294737.534000] apm: overridden by ACPI.
  debian_version is not yet providing pre-compiled drivers for WinModems

<end paste>

I have tried to follow instructions found by googling, but I'm afraid there seem to be several different sets of instructions available & none I've found that are at my very basic level of understanding. What I really need is for someone to give me a step by step type of direction ie: open this, type that, hit enter, reboot, etc.

I really want to thank anyone who will take thier time to help me with this, as dial-up is my only option for these machines.

---

### Post by towsonu2003 on 2006-05-07
[QUOTE=ttt06][quote=ModemData.txt]
 [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) has good general guidance.

*snip*

 The potentially supporting drivers now loaded on this System are:
0 snd_es1968

*snip*

 The kernel was assembled with compiler:  3.4.5
 with current System compiler GCC=4.0.2

*snip*
	  
 The modem has a supported Lucent/Agere DSP (digital signal processing) Mars or Apollo DSP
 (digital signal processing) chipset with primary PCI_ID:  11c1:0445
 DSP=1

Support packages for 2.6.n kernels are at:
[http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/) with folders for
	debian/  containing some installers
	ubuntu/  containing some installers
The ltmodem-8.26b1.tar.gz  and ltmodem-8.31b1.tar.gz are driver compiling resources,
with the 8.31 having support for SMP (symmetric multi processor) motherboards.[/quote]
[/QUOTE]
above are the crucial sections for you. See the second link in my signature (same link given above in quote) for the section "Modems supported by the Lucent driver". Good luck :)

---

