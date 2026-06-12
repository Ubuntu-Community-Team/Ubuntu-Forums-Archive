---
title: "Agere modem help?"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by randyh on 2006-07-04
Newbe here, 
  I have read and dont understand the messages in the modem.txt file. seems to say it might work and seems to say it won't work. Can someone help me clear it up.
 will it work or do i need to find a different modem?
 
Thanks in advance!
Randy
 
Here is the text.

 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 6.06 LTS  kernel 2.6.15-23-386  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_July_01
------------ --------------  System information ------------------------
 Ubuntu 6.06 LTS 
 on System with processor: i686
 currently under kernel:   2.6.15-23-386

 [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) has good general guidance.
 Be sure to read the Ethernet section of Modem/YourSystem.txt 
DEVPPP=crw------- 1 root root 108, 0 2006-05-30 21:15 /dev/ppp
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
	Reading /proc/asound/pcm 
00-00: Intel ICH : NVidia nForce : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : NVidia nForce - MIC ADC : capture 1
00-02: Intel ICH - IEC958 : NVidia nForce - IEC958 : playback 1
 The potentially supporting drivers now loaded on this System are:
0 snd_intel8x0


 The kernel was assembled with compiler:  4.0.3
 a gcc-4.0.3  package must be installed to support driver compiling
-------------
 Compiling utility   make   Not found.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:01:06.0
    
Providing detail for device at  0000:01:06.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 11c1:048c   Communication controller: Agere Systems V.92 56K WinModem (rev 03)
  SubSystem 11c1:044c  Agere Systems: Unknown device 044c
	Flags: bus master, medium devsel, latency 64, IRQ 5
 Checking for IRQ 5 sharing with modem.
IO-APIC-edge  ide1
O-APIC-level  eth0

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:048c 11c1:044c debian_version 2.6.15-23-386  4.0.3 none    i686
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  [http://www.agere.com/client/modem_dsp.html](http://www.agere.com/client/modem_dsp.html). Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
   
 Lucent/Agere Mars/WinModem drivers from version 8.30 onwards have
 the necessary fix for SMP machines which includes machines with
 hyperthreading turned on (virtually acting as two CPUs).
 

  Class 0703:  11c1:048c is still NOT supported under Linux, as of 2006_July_01
  It is a "software" modem without a digital signal processing (DSP) chipset.
  The ltmodem drivers from [http://ltmodem.heby.de](http://ltmodem.heby.de) resources for DSP modems do NOT provide support,
    A dialout terminates with "No Carrier" or a Hang if usage of the ltmodem drivers is attempted. See InfoGeneral.txt about alternatives.


  ======= PCI_ID checking completed ====== 
 Update=2006_July_01
A PCMCIA CardBus is not detected on this System.
 Checking for modem symbolic link support lines within /etc/udev/ files


Checking the /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted



deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling


      
 The Major.Minor versions differ in the designated compiler none and the 4.0.3 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See [http://linmodems.technion.ac.il/archive-fifth/msg04252.html](http://linmodems.technion.ac.il/archive-fifth/msg04252.html) 
 
Kernel-header resources needed for compiling are not manifestly ready!
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.15-23-386    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu 		linux-headers-2.6.15-23-386		[http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.15-23-386	   If not present on install CDs search
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		kernel-source-2.6.15-23-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.15-23-386 or kernel-smp-devel-2.6.15-23-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.15-23-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

 A /dev/modem symbolic link is not set.

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
-------------------------------------
 Resident PPP support modules are properly uncompressed .
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:E0:18:F5:CF:6B  
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/YourSystem.txt
 ---- dmesg queries -------
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[4294668.507000] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 18) *0, disabled.
[4294668.508000] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 18) *0, disabled.
[4294668.508000] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 18) *0, disabled.
[4294668.510000] ACPI: PCI Interrupt Link [LNKM] (IRQs 20 21 22) *0, disabled.
[4294668.533000]   PREFETCH window: disabled.
[4294668.533000]   IO window: disabled.
[4294668.534000] audit: initializing netlink socket (disabled)
[4294697.101000] ibm_acpi: ec object not found
[4294697.126000] pcc_acpi: loading...
[4294702.835000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294702.835000] apm: overridden by ACPI.

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the [http://www.smlink.com](http://www.smlink.com)  slmodem software.
  Check pppd version with:
    pppd --version
  See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)
    
  debian_version is not yet providing pre-compiled drivers for WinModems

---

### Post by randyh on 2006-07-05
I am still lost.

Any help?

Randy

---

### Post by delphi on 2006-07-06
Try:

( [http://ubuntuforums.org/showthread.php?t=198730&highlight=ltmodem](http://ubuntuforums.org/showthread.php?t=198730&highlight=ltmodem) )

Worked fine for me.

---

