---
title: "Modem/connecting to internet?"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by Locke897 on 2005-04-25
Hi,

I'm a newbie just moving over to Linux from Windows, and I've installed Ubuntu 5.04 but do not know how to connect to the internet. My computer is a Compaq Presario 5441 (476 Mhz, 184MB RAM, SiS 530 integrated graphics). I've looked around on linmodems.org and used their scanModem tool. Here is the output file ModemData.txt: 


DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.04 kernel 2.6.10-5-386
 Occassionally reponses are blocked by an Internet Providers mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_April_19
------------ --------------  System information ------------------------
Ubuntu 5.04 "Hoary Hedgehog" 
 on System with processor: i586
 currently under kernel:   2.6.10-5-386

There are emerging complications under 2.6.10 kernels.  Concerning code for:
Smartlink slmodem :
   slmodem-2.9.9b.tar.gz at [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
      has the current fixes.  Related messages are:
   [http://www.datiku.com/documents/2610_migration.php](http://www.datiku.com/documents/2610_migration.php)
   [http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html) 
   [http://linmodems.technion.ac.il/archive-fourth/msg03736.html](http://linmodems.technion.ac.il/archive-fourth/msg03736.html) . 
Lucent/Agere DSP/ltmodem:
  [http://linmodems.technion.ac.il/archive-fourth/msg03733.html](http://linmodems.technion.ac.il/archive-fourth/msg03733.html) 
Concerning Intel-536ep and 537
   [http://linmodems.technion.ac.il/archive-fifth/msg00280.html](http://linmodems.technion.ac.il/archive-fifth/msg00280.html)
   [http://linmodems.technion.ac.il/archive-fifth/msg00881.html](http://linmodems.technion.ac.il/archive-fifth/msg00881.html)
   
 The kernel was assembled with compiler:  3.3.5
 a gcc package must be installed to support driver compiling

Checking for kernel-headers needed for compiling.
Kernel-header resources are not evident.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.10-5-386    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)
 Ubuntu 		linux-headers-2.6.10-5-386		[http://www.ubuntulinux.org/community/ConfigUbuntu5.04%20repositories](http://www.ubuntulinux.org/community/ConfigUbuntu5.04%20repositories)
    Debian & Ubuntu will also require kernel-kbuild package installation
 Mandrake 	kernel-source-2.6.10-5-386	   If not present on install CDs search
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		linux-2.6.10-5-386				, ????  , kernels are named k_deflt
One of which must be installed if compiling drivers to match kernel 2.6.10-5-386 proves necessary.
This is necessary for most modem drivers, through some Linux distributions provide some compiled drivers.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
  

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  0000:00:09.0
    
Providing detail for device at PCI_bus 0000:00:09.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 11c1:0441   Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
  SubSystem 144f:110d   Askey Computer Corp. Lucent Win Modem
0000:00:09.0 0780: 11c1:0441 (rev 01)
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at e4901000 (32-bit, non-prefetchable) [size=256]
	I/O ports at d000 [size=8]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:0441 144f:110d debian 2.6.10-5-386 3.3.5     i586

 == Checking PCI IDs through modem chip suppliers ==

 The modem has a supported Lucent/Agere DSP (digital signal processing) chipset
  with primary PCI_ID:  11c1:0441
 DSP=1

 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  [http://www.agere.com/client/modem_dsp.html](http://www.agere.com/client/modem_dsp.html). Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
 
 Call waiting specified by, +pcw=1, is not implmented in the ltmodem drivers.
Configuration with forcing is described in: [http://linmodems.technion.ac.il/archive-fifth/msg00055.html](http://linmodems.technion.ac.il/archive-fifth/msg00055.html)
 0x0441 -- Mars 2 - data/fax only

 Support has been extended to 2.6.n kernels by Rajesh K. Balan and
 Aleksey Kondratenko <alk@tut.by>, with official support from AgereSystems later following.
 Functionality requires serial_core support, either as a module or integral to the kernel.
 
 The ltmodem-2.6-alk-7.tar.bz2 can be downloaded from:
   [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/) 
   with low bandwidth alternate: [http://alk.at.tut.by/ltmodem-2.6-alk-7.tar.bz2](http://alk.at.tut.by/ltmodem-2.6-alk-7.tar.bz2)
   There are detailed instructions in  [http://linmodems.technion.ac.il/archive-fifth/msg00584.html](http://linmodems.technion.ac.il/archive-fifth/msg00584.html)
   
   For kernels prior to 2.6.11, the resources at [http://ltmodem.heby.de](http://ltmodem.heby.de) can be utilized.
   
   If service cannot be established under an SMP kernel, try a uniprocessor kernel instead.  See:
   [http://linmodems.technion.ac.il/archive-fifth/msg01278.html](http://linmodems.technion.ac.il/archive-fifth/msg01278.html)



 Add either of the following lines to the Debian  /etc/apt/sources.list
 to enable automatic updates on installer availability:
   deb [http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/) ./
   deb [http://www.sfu.ca/~cth/ltmodem/dists/debian/](http://www.sfu.ca/~cth/ltmodem/dists/debian/) ./


  The desired installer name is like:
========================================
ltmodem-2.6.10-5-386_8.nn_i386.deb
----------------------------------------
 ltmodem-kv-Kernel_FL-LTver--.CPU.rpm   explains the versioning.
 For your System
            Kernel_FL is 2.6.10-5-386 , the full kernel version displayed by: uname -r
                      LTver is 8.31a9, the release of the compiler kit
                               8.nn is the Agere core code designation.
       The proccesor type or CPU is:  i586      dispayed by:  uname -m
 used in compiling and assembling driver packages.

      
 A suitable installer is not available as of this 2005_April_19 update.
 Check in the section debian at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
   for a subsequent Installer submission.
 Older releases have been archived at:
   [http://linmodems.technion.ac.il/packages/ltmodem/archive/](http://linmodems.technion.ac.il/packages/ltmodem/archive/)
 Also there is a RPM search engine at:   [http://rpm.pbone.net](http://rpm.pbone.net)
 The closest match to your   i586=CPU   is recommended.
   The closest match to your   i586=CPU   is recommended.
   For example replacements in order of preference for an
     i686 would be i586, i486 and i386
 If not present use the  ltmodem-8.31a9.tar.gz compiler kit.

 The list of available Installers for debian as of this 2005_April_19
 is inserted into to Modem/General.txt
  ======= PCI_ID checking completed ====== 
 Update=2005_April_19
A PCMCIA CardBus is not detected on this System.
GCCversion=
   
For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere DSP modems
   
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias char-major-108 ppp_generic
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/General.txt
DEVPPP=crw------- 1 root root 108, 0 2005-04-25 10:56 /dev/ppp
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
No local APIC present or hardware disabled
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
audit: initializing netlink socket (disabled)
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
    ACPI-0686: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[ 7], disabling event
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
  debian is not yet providing pre-compiled drivers for WinModems


My modem is apparently a Lucent Microelectronics 56K Winmodem, but I haven't been able to find a driver for it, and even if I do, I don't know how to install it. The modem is detected in Device Manager, but under "Device" is listed as unknown. Also, once the modem is properly configured, where/how do I dial into the Internet (do I need any settings from my ISP)? Thanks in advance for any replies.

---

### Post by az on 2005-04-25
[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)

---

