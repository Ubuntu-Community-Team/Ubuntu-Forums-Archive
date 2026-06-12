---
title: "Modem &amp; Winfax Replacement for Acer 4062NLCi"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by handilin on 2006-06-30
I tried Ubuntu 6.06 LiveCD so far i satisfy with this Linux OS, but i still miss the Modem and software that can replace Winfax. I am using my laptop as a fax machine so it's hard for me to switch to Ubuntu when this software is not available. Anyone can help me out? 
Also i have problem reading the ModemData.txt from scanmodem script. Which linmodem driver should i use? I attach the modemdata.txt below.

- Handi -

Code updated on:  2006_June_14
------------ --------------  System information ------------------------
 Ubuntu 6.06 LTS 
 on System with processor: i686
 currently under kernel:   2.6.15-23-386

 [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) has good general guidance.
 Be sure to read the Ethernet section of Modem/YourSystem.txt 
DEVPPP=crw------- 1 root root 108, 0 2006-05-31 01:15 /dev/ppp
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Reading /proc/asound/pcm 
00-00: ALC260 Analog : ALC260 Analog : playback 1 : capture 1
00-01: ALC260 Analog : ALC260 Analog : capture 1
 The potentially supporting drivers now loaded on this System are:
0 snd_hda_intel


 The kernel was assembled with compiler:  4.0.3
 a gcc-4.0.3  package must be installed to support driver compiling
-------------
 Compiling utility   make   Not found.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:00:1b.0
    
Providing detail for device at  0000:00:1b.0
  with vendor-ID:device-ID
	    ----:----
Class 0403: 8086:2668   0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
  SubSystem 1025:008f  Acer Incorporated [ALI]: Unknown device 008f
	Flags: bus master, fast devsel, latency 0, IRQ 177
 Checking for IRQ 177 sharing with modem.
O-APIC-level  uhci_hcd:usb4, eth0, HDA Intel, i915@pci:0000:00:02.0

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:2668 1025:008f debian_version 2.6.15-23-386  4.0.3 none    i686
The audio card 8086:2668 may carry a soft modem chip.
	Reading /proc/asound/card0/codec#1
Codec: Generic 14f1 ID 2bfa
Address: 1
Vendor Id: 0x14f12bfa
Subsystem Id: 0x1025008f
Revision Id: 0x90000
The audio/modem driver is not competent to write soft modem information to /proc/asound/pcm 
----------------
for High Definitiona Audio (HDA) cards with an embedded Conexant softmodem chip, a 2.6.16 kernel or later is required for use with the HSF modem driver version 7.47.00.01.

For a crash issue with the 2.6.16 kernel, please make sure that your
kernel was not compiled with the CONFIG_4KSTACKS option is not set as
the HSF modem driver is known to requires more than 4K of stacks in a
few cases.

If you require more assistance, please send at [email]support@linuxant.com[/email] the
output of 'dumpdiag'. Type the following in a root shell:

    hsfconfig --dumpdiag

If this command crashes your machine, please try instead:

    hsfconfig --dumpdiag --noprobe

Just send us the generated file located in /tmp ('hsfdiag.txt').
------------------


ALSA modem support within the snd-hda-intel driver is included in 2.6.14 and later kernels.
----------------
For any High Definitiona Audio (HDA) cards with an embedded Conexant softmodem chip, 
a 2.6.16 kernel or later is required for use with the HSF modem driver version 7.47.00.01.

If there is a crash issue with the 2.6.16 kernel, please make sure that your
kernel was not compiled with the CONFIG_4KSTACKS option is not set.
The HSF modem driver is known to requires more than 4K of stacks in a few cases.

If you require more assistance, please send to [email]support@linuxant.com[/email] the
output of 'dumpdiag'. Type the following in a root shell:
    hsfconfig --dumpdiag
If this command crashes your machine, please try instead:
    hsfconfig --dumpdiag --noprobe
Just send to [email]support@linuxant.com[/email] the hsfdiag.txt written in  the /tmp/ folder.
------------------

              From records, 1025:008f has soft modem codec type ConexantHDA
The following two Root commands should set up the modem if it is not a Conexant type.
	sudo modprobe snd-hda-intel
	sudo slmodemd --alsa -c YOUR_COUNTRY hw:0,1
Get the SLMODEMD.gcc4.tar.gz from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
       
 The controller: 8086:2668 Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
 is capable of supporting soft modem chips from AT LEAST manufacturers:
	Conexant
 The Subsystem PCI id does not itself identify the modem Codec.
Checking for autoloaded ALSA modem drivers
snd_hda_intel          18964  1 
snd_hda_codec         142640  1 snd_hda_intel
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm

  Driver snd-hda-intel  may enable codec acquisition 
Checking for modem on HDA audio card
 ----- /proc/asound/card0/codec#1 -----
Codec: Generic 14f1 ID 2bfa
Address: 1
Vendor Id: 0x14f12bfa
Subsystem Id: 0x1025008f
Revision Id: 0x90000
 ----- /proc/asound/pcm -----
00-00: ALC260 Analog : ALC260 Analog : playback 1 : capture 1
00-01: ALC260 Analog : ALC260 Analog : capture 1
  === Begin mc97 codec query  ===
--- /proc/asound/card0/codec#1 --- 
Codec: Generic 14f1 ID 2bfa
Address: 1
Vendor Id: 0x14f12bfa
Subsystem Id: 0x1025008f
Revision Id: 0x90000
  has a Conexant codec
----------------------------------- 
	   
 Files under /proc/asound/ do not include  modem codec information. 
 If more decisive information is not given below,
 this is a tentative signature of a Conexant hsfmodem.  Download a hsfmodem package from
 [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers) or your installation CDs.  For SuSE/Novell, install both
 km_hsfmodem and hsfmodem packages,  for drivers and configuration tools respectively.
 
  === End mc97 codec query  ===

 Beginning check for older ac97_codec modems.
 An older ac97_modem codec was not detected.

 There are the following routes toward support:
	Follow instructions in Modem/SoftModem.txt for identifying the modem under a Microsoft boot.
  Test the effectiveness of the hsfmodem package from [http://www.linuxant.com/drivers/hsf/index.php](http://www.linuxant.com/drivers/hsf/index.php).
      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor=1025 is Acer, [http://global.acer.com/](http://global.acer.com/) PC and latop manufacturer with devices including:
 . 1025:5453   M5453 AC-Link Controller Modem Device
 . 1025:0038   an AC97 link modem.


 Under the controller 8086:2668 Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller,
 with modem subSystem 1025:008f     
 Alternative supporting packages are the SmartLink slmodem-2.9.n using its proprietary slamr driver, 
 or dependent on  8086:2668 Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller, an  Open Source driver from the  ALSA package.
 See Modem/Slmodem-ALSA.txt for details.
 A sample compilation is shown in: [http://linmodems.technion.ac.il/archive-fifth/msg02567.html](http://linmodems.technion.ac.il/archive-fifth/msg02567.html)
  
 For SuSE 9.2 users, there is an update  for driver slamr.ko loading during bootup. 
 To find it easily, search for "slamr" within  [http://www.novell.com/linux/download/updates/92_i386.html](http://www.novell.com/linux/download/updates/92_i386.html)
     
 == Checking PCI IDs through modem chip suppliers ==

 Vendor=8086 is Intel, Inc. producing HaM and 536ep host controller free (HCF) modems, 537 soft modem
[http://developer.intel.com/design/modems/](http://developer.intel.com/design/modems/) .  Also produced are
AC97 and MC97 controllers managing a varierty of non-Intel soft modem Subsystems.
 These subSystems often have PCI_IDs assigned by the modem assembler, rather than the chip provider.
 Download Intel-537ep drivers through:  [http://developer.intel.com/design/modems/support/drivers.htm](http://developer.intel.com/design/modems/support/drivers.htm)  
 Also check at: [http://linmodems.technion.ac.il/packages/Intel/537/](http://linmodems.technion.ac.il/packages/Intel/537/)  
 for beta releases and perhaps Already compiled drivers for some Linux distributions
 A very detailed installation report cogent to 537 type modems is at:
                  [http://linmodems.technion.ac.il/archive-fifth/msg00541.html](http://linmodems.technion.ac.il/archive-fifth/msg00541.html)

 Setup call id with:
 	Type 1 : When the phone line is not in use                    at+vcid=1
	Type 2 : When the phone line is already in use on a call      at+pcw=0
 ---------------------

  ======= PCI_ID checking completed ====== 
 Update=2006_June_14

Analyzing information for PCMCIA device at PCI Bus 06:01.0
0000:06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
	Subsystem: Acer Incorporated [ALI]: Unknown device 008f
	Flags: bus master, medium devsel, latency 168, IRQ 185
GREPping for an inserted PCMCIA modem with filter:        ommunication
 If a PCMCIA modem is currently inserted and the sockets activated by
    /etc/init.d/pcmcia start
 then the PCMCIA bridge is NOT transparent.

 If the modem is known to have a Lucent digital signal processing chipset,
 then PCMCIA.tar.gz variant assembled by Joern Wustenfeld is necessary,
 rather than the standard ltmodem-8.31b1.tar.gz at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
 Checking for modem symbolic link support lines within /etc/udev/ files


Checking the /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted


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
eth0      Link encap:Ethernet  HWaddr 00:16:36:05:80:87  
eth1      Link encap:Ethernet  HWaddr 00:13:CE:7C:84:23  
          inet6 addr: fe80::213:ceff:fe7c:8423/64 Scope:Link
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/YourSystem.txt
 ---- dmesg queries -------
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[4294668.155000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[4294668.155000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[4294668.155000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[4294668.191000]   IO window: disabled.
[4294668.191000]   MEM window: disabled.
[4294668.191000]   PREFETCH window: disabled.
[4294668.191000]   IO window: disabled.
[4294668.191000]   MEM window: disabled.
[4294668.191000]   PREFETCH window: disabled.
[4294668.191000]   IO window: disabled.
[4294668.191000]   MEM window: disabled.
[4294668.191000]   PREFETCH window: disabled.
[4294668.192000] audit: initializing netlink socket (disabled)
[4294802.574000] ibm_acpi: ec object not found
[4294802.593000] pcc_acpi: loading...
[4294825.666000] apm: BIOS not found.

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the [http://www.smlink.com](http://www.smlink.com)  slmodem software.
  Check pppd version with:
    pppd --version
  See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)
    
  debian_version is not yet providing pre-compiled drivers for WinModems

---

