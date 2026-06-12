---
title: "ESS modem - am I ought of luck?"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by OMRebel on 2006-04-13
I have a HP Pavilion n5150 laptop, that has a built in ESS modem.  I am trying to get my modem working, but no luck so far.  It is showing up under device manager, but when I try to set it up under networking, it cannot find the port.  I did some searching on the web, and came across this page here:

[http://wettstein.homelinux.org/ess/](http://wettstein.homelinux.org/ess/)

I'm running Breezy on my laptop.  Am I just out of luck with this modem, or is there a way to get it working?

Thanks!

---

### Post by OMRebel on 2006-04-13
Well, I found my answer.  I am out of luck.  Used the scanModem utility from linmodems.org:
```

DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-10-386  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at DISCUSS@linmodems.org
Code updated on:  2006_April_07
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-10-386

 https://wiki.ubuntu.com/DialupModemHowto has good general guidance.
 Be sure to read the Ethernet section of Modem/YourSystem.txt 
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:08.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
	Reading /proc/asound/pcm 
00-00: Allegro : Allegro : playback 2 : capture 1
 The potentially supporting drivers now loaded on this System are:
0 snd_maestro3


 The kernel was assembled with compiler:  3.4.5
 a gcc-3.4.5  package must be installed to support driver compiling
To support compiling, get the  BreezyGCC_3.4_i386.tar.gz from http://phep2.technion.ac.il/linmodems/packages/smartlink/ 
-------------
 Compiling utility   make   Not found.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:00:08.1
    
Providing detail for device at  0000:00:08.1
  with vendor-ID:device-ID
	    ----:----
Class 0780: 125d:1989   Communication controller: ESS Technology ESS Modem (rev 12)
  SubSystem 103c:0012  Hewlett-Packard Company: Unknown device 0012
	Flags: medium devsel, IRQ 5
 Checking for IRQ 5 sharing with modem.
      XT-PIC  uhci_hcd:usb1, Allegro
      XT-PIC  ide1

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 125d:1989 103c:0012 debian_version 2.6.12-10-386  3.4.5 none    i686
      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor=125d is ESS Technologies, making devices:
 There has been no formal support for Linux since kernels 2.2.2
 There is no hope for support under 2.6.n kernels.
 See InfoGeneral.txt about alternatives.

 Only under 2.4.n Linux kernels and are there some kludges of fadding utility:
   http://linmodems.technion.ac.il/archive-fourth/msg00317.html   (2004Feb08)
   http://andrew.cait.org/ess/
   http://sidlo.penguin.cz/ES2838/index_en.html
   http://tx.technion.ac.il/~raindel/
   http://phep2.technion.ac.il/linmodems/archive/msg04424.html


  ======= PCI_ID checking completed ====== 
 Update=2006_April_07

Analyzing information for PCMCIA device at PCI Bus 00:04.0
0000:00:04.0 CardBus bridge: Texas Instruments PCI1420
	Subsystem: Hewlett-Packard Company: Unknown device 0014
	Flags: bus master, medium devsel, latency 168, IRQ 11
GREPping for an inserted PCMCIA modem with filter:        ommunication

Analyzing information for PCMCIA device at PCI Bus 00:04.1
0000:00:04.1 CardBus bridge: Texas Instruments PCI1420
	Subsystem: Hewlett-Packard Company: Unknown device 0014
	Flags: bus master, medium devsel, latency 168, IRQ 11
GREPping for an inserted PCMCIA modem with filter:        ommunication
 A PCMCIA modem is detected.
      
 The stardard ltmodem resources should suffice for modem support:
     http://ltmodem.heby.de/
 if the modem has a Lucent/Agere digital processing chipset.
 
drwxr-xr-x  2 root root 0 2006-04-13 09:15 /dev/.udevdb

There is an active UDEV file system, creating device nodes in volatile RAM.
For SmartLink modems using the slamr.ko or slusb.ko drivers an /etc/init.d/ script
will be necessary to create /dev/slamr0 or /dev/slusb0 ports, or manually by:
#  mknod -m 600 /dev/slamr0 c 242 0
#  mknod -m 600 /dev/slusb0 c 243 0
upon each bootup.

For information on modem port creation under the UDEV device file system see:
   http://linmodems.technion.ac.il/archive-fourth/msg03299.html  for Conexnant modems
   http://linmodems.technion.ac.il/archive-fifth/msg01177.html  for Lucent/Agere DSP modems
   
 Checking for modem symbolic link support lines within /etc/udev/ files


Checking the /etc/apt/sources.list
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main


deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://theli.free.fr/packages/breezy/ ./

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling


      
 The Major.Minor versions differ in the designated compiler none and the 3.4.5 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See http://linmodems.technion.ac.il/archive-fifth/msg04252.html 
 
Kernel-header resources needed for compiling are not manifestly ready!
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.12-10-386    	http://www.debian.org/distrib/packages or install CD
 Ubuntu 		linux-headers-2.6.12-10-386		http://http://packages.ubuntu.com/ or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.12-10-386	   If not present on install CDs search
 	http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/ 
	http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html, or other mirrors.
  SuSE		kernel-source-2.6.12-10-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.12-10-386 or kernel-smp-devel-2.6.12-10-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.12-10-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

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
eth0      Link encap:Ethernet  HWaddr 00:E0:98:90:E9:12  
          inet6 addr: fe80::2e0:98ff:fe90:e912/64 Scope:Link
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/YourSystem.txt
 ---- dmesg queries -------
[4294673.188000] audit: initializing netlink socket (disabled)
[4294727.625000] ibm_acpi: ec object not found
[4294743.579000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294743.579000] apm: overridden by ACPI.

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the http://www.smlink.com  slmodem software.
  Check pppd version with:
    pppd --version
  See  http://linmodems.technion.ac.il/archive-fourth/msg03167.html
    
  debian_version is not yet providing pre-compiled drivers for WinModems

```
If I'm reading the above correclty, then no soup for me! ](*,)

---

### Post by az on 2006-04-13
No soup for you.  I threw one of those modems out the window back in 2001....

---

### Post by OMRebel on 2006-04-13
What would you recommend for my notebook?  It would be nice if I could just open my laptop and swap that modem out for a different one that would work, but doubt that's possible.  Any good PCMCIA modems that work flawlessly under Ubuntu?

---

### Post by helmut_hed on 2006-04-30
Wait, it's not too late!  There is a new driver recently released for ESS:

[http://tx.technion.ac.il/~raindel/ess_2.6-v0.1.tar.gz](http://tx.technion.ac.il/~raindel/ess_2.6-v0.1.tar.gz)

installation process is:

tar xvzf ess_2.6-v0.1.tar.gz
cd ess_2.6-v0.1
su
(type your root password)
./setup

which will compile, install, and activate the driver.  Please let me know the results.

Best regards,
Jeff Trull
(driver maintainer)

---

### Post by OMRebel on 2006-05-11
I was skimming through some old threads and just now saw your reply.  I will give it a shot and let you know how it goes.  I will give this a shot tonight and post the results.  Thanks!

---

### Post by helmut_hed on 2006-05-11
I'm afraid I have to update the instructions I gave you.  I only recently installed Ubuntu, and the instructions were a bit too generic.  Anyway, follow this HOWTO:

[http://ubuntuforums.org/showthread.php?t=171163](http://ubuntuforums.org/showthread.php?t=171163)

but make the following substitutions:

1) the lspci output you are looking for is "125d:2898", not "134d:789*"
2) download the driver from the location in my previous post
3) use that file instead of pctel-0.9.7-9-rht-5.tar.gz

I look forward to hearing your results.

Regards,
Jeff Trull

---

### Post by OMRebel on 2006-05-11
I tried the very first step, and I got:

bash: /sbin/lspci: No such file or directory

So, I tried just lspci, and for the modem it gave me:
0000:00:08.1 Communication controller: ESS Technology ESS Modem (rev 12)

I then tried:
brad@ubuntu:~$ lspci -d 125d: -n
0000:00:08.0 0401: 125d:1988 (rev 12)
0000:00:08.1 0780: 125d:1989 (rev 12)

I'm gonna try anyways, even though it gives me 1989

---

### Post by OMRebel on 2006-05-11
checking for running kernel version...2.6.12
checking for gcc...3.4.5
searching for kernel includes...found at /usr/src/linux-headers-2.6.12-9/include/
checking for autoconf.h.../usr/src/linux-headers-2.6.12-9/include//linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in version.h...UTS_RELEASE is 2.6.12-9
checking type of tty_struct.count...int
checking for presence of udev...present
detecting your modem...** error
the supported modem (ESS Technology ES2898) is not present on your system
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.  A transcript of the build process
has been saved in make.log.  When reporting problems to
the development team, please send us this file.

Well, that bites.  Is there anyway I can get around this to get it installed?

---

### Post by OMRebel on 2006-05-11
I emailed ya the make.log to see if you know of a way to get this going.  If not, then I appreciate you trying to help man.

---

### Post by helmut_hed on 2006-05-11
Oh no, unfortunately it's *not* OK.  You don't have a supported modem.  In retrospect I can see that clearly from your scanmodem output!  I'm sorry to get your hopes up and then dash them like that.

The pci output would have to read "125d:2898".

Sorry about that.

Jeff

---

