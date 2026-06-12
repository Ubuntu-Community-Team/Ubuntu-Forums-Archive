---
title: "Can't get my modem to work- Toshiba Satellite 1800"
date: 2006-07-01
forum: Hardware &amp; Laptops
---

### Post by sonoftheclayr on 2006-07-01
I have a Toshiba Satellite 1800 and have tried just about anything to get my modem working.
It is a Toshiba Software AMR modem if that is any help and here is my ScanModem output:
```


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at DISCUSS@linmodems.org
Code updated on:  2006_April_11
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386

 https://wiki.ubuntu.com/DialupModemHowto has good general guidance.
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
	Reading /proc/asound/pcm 
00-00: ALI 5451 : ALI 5451 : playback 32 : capture 1
00-01: ALI 5451 modem : ALI 5451 modem : playback 1 : capture 1

The modem is supported by an ALSA modem driver plus slmodemd, 
OR alternatively (not both) by
an hsfmodem package from http://www.linuxant.com/drivers. Further diagnostics
below may resolve between the two.
ALSA modem drivers are included in 2.6.n kernel packages and currently include:
	snd-hda-intel, a joint audio + modem driver
	snd-ali5451  ,        "             "
	intel8x0m        , depending on intel8x0    audio driver
	snd_via82xx_modem,          "   snd_via82xx   "
	snd-atiixp-modem ,          "   snd-atiixp    "
Driver loading itself does NOT resolve between ALSA and hsfmodem alternatives. 

 The potentially supporting drivers now loaded on this System are:
0 snd_ali5451


 The kernel was assembled with compiler:  3.4.5
 a gcc-3.4.5  package must be installed to support driver compiling
To support compiling, get the  BreezyGCC_3.4_i386.tar.gz from http://phep2.technion.ac.il/linmodems/packages/smartlink/ 
-------------
 Compiling utility   make   Not found.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:00:06.0
    
Providing detail for device at  0000:00:06.0
  with vendor-ID:device-ID
	    ----:----
Class 0401: 10b9:5451   Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
  SubSystem 1179:0001  Toshiba America Info Systems: Unknown device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 11
 Checking for IRQ 11 sharing with modem.
      XT-PIC  ohci_hcd:usb1, ALI 5451, yenta, yenta

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 10b9:5451 1179:0001 debian_version 2.6.12-9-386  3.4.5 none    i686
The audio card 10b9:5451 may carry a soft modem chip.
-------------------------------
The modem should be setup by:
     sudo slmodemd --alsa -c YOUR_COUNTRY ProxyDevice
Get the SLMODEMD.gcc3 from http://linmodems.technion.ac.il/packages/smartlink/
and follow guidance therein.
	The soft modem in the 8086:2668 High Definition Audio has low level support by 
the snd-hda-intel driver, beginning with the 2.6.14 kernels.  
        The Conexant soft modem chipset is not supported by snd-hda-intel.

----------------
for High Definitiona Audio (HDA) cards with an embedded Conexant softmodem chip, a 2.6.16 kernel or later is required for use with the HSF modem driver version 7.47.00.01.

For a crash issue with the 2.6.16 kernel, please make sure that your
kernel was not compiled with the CONFIG_4KSTACKS option is not set as
the HSF modem driver is known to requires more than 4K of stacks in a
few cases.

If you require more assistance, please send at support@linuxant.com the
output of 'dumpdiag'. Type the following in a root shell:

    hsfconfig --dumpdiag

If this command crashes your machine, please try instead:

    hsfconfig --dumpdiag --noprobe

Just send us the generated file located in /tmp ('hsfdiag.txt').
------------------

 For snd-ali5451.ko compiling instructions, see http://phep2.technion.ac.il/linmodems/archive/msg04955.html.
Modem support within the snd-ali5451 driver is included in some 2.6.12 and later kernels
The following two Root commands should set up the modem.
	sudo modprobe snd-ali5451
	sudo slmodemd --alsa -c YOUR_COUNTRY -s hw:0,1
Get the SLMODEMD.gcc3.tar.gz from http://linmodems.technion.ac.il/packages/smartlink/
       
 The controller: 10b9:5451  ALI 5451 
 is capable of supporting soft modem chips from AT LEAST manufacturers:
	AgereSystems
	Conexant
	Smartlink
 The Subsystem PCI id does not itself identify the modem Codec.
Checking for autoloaded ALSA modem drivers
snd_ali5451            22596  1 
snd_ac97_codec         72188  1 snd_ali5451
snd_pcm                78344  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd                    48644  8 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

  Driver snd-ali5451  may enable codec acquisition 
  === Begin mc97 codec query  ===
 the MC97 file is:	/proc/asound/card0/codec97#0/mc97#1-1
 --------
1-1/0: Silicon Laboratory Si3036,8 rev 7

Extended modem ID: codec=1 LIN1
Modem status     : GPIO MREF ADC1 DAC1 PRE(ADC2) PRF(DAC2) PRG(HADC) PRH(HDAC)
Line1 rate       : 8000Hz
 --------
 from /proc/asound/card0/codec97#0/mc97#1-1+regs
    0:7c = 5349
    0:7e = 4c27
    Translating into:  SIL27
an AgereSystems codec
  === End mc97 codec query  ===

 Beginning check for older ac97_codec modems.
 An older ac97_modem codec was not detected.

 The Subsystem has an Agere Systems codec SIL27

 The modem can be set up by Root commands:
   sudo modprobe snd-ali5451
   sudo slmodemd --alsa -c YOUR_COUNTRY -s hw:0,1
 
 The ALSA modem driver snd-ali5451 provides low level hardware access.
 The slmodemd provides high level functions and is  not kernel-version specific.
 From http://linmodems.technion.ac.il/packages/smartlink/   follow the link 
 SLMODEMD.gcc3.tar.gz 
 Also download the ungrad-winmodem.tar.gz and the http://linmodems.technion.ac.il/packages/unloading.gz
 Within the SLMODEMD package the 1st_Read.txt gives instructions 
 For guidance on bootup automation see:
   http://linmodems.technion.ac.il/archive-fifth/msg04652.html
 
	Read Modem/Slmodem.txt instruction for doing the slamr diagnostic.
 == Checking PCI IDs through modem chip suppliers ==

 SmartLink at http://www.smlink.com/ owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  http://www.smlink.com/main/index1.php?ln=en&main_id=40
 But a more recent code and a much broader license for other chipset support,
 can be downloaded from http://linmodems.technion.ac.il/packages/smartlink/  
 Though not always needed, download the files: 
   slmodem-CurrentVersion.tar.gz - provides the most general code package.
   SLMODEMD.gcc3 - provides a compiled slmodemd 
   ungrab-winmodem.tar.gz  -  may be needed for usage with slamr. 
 Details on their usage are in Slmodem.txt, Slmodem-ALSA.txt and
 http://linmodems.technion.ac.il/slmodem-serial.html

 == Checking PCI IDs through modem chip suppliers ==

 Vendor 10b9 is Acer Labs, producing highly integrated motherboards and Ali components.
 The tight integration unfortunately ofter blocks identification of the modem chipset.
 Desired information may be gained by using a COMM console under MS Windows,
   and using ATI commands to elicit chipset and driver information.
 10b9:5450  ALI 5450 and  10b9:5451  ALI 5451 are controllers for unsupported "sound  modems"
 

  ======= PCI_ID checking completed ====== 
 Update=2006_April_11

Analyzing information for PCMCIA device at PCI Bus 00:11.0
0000:00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
	Subsystem: Toshiba America Info Systems: Unknown device 0001
	Flags: bus master, slow devsel, latency 168, IRQ 11
GREPping for an inserted PCMCIA modem with filter:        ommunication

Analyzing information for PCMCIA device at PCI Bus 00:11.1
0000:00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
	Subsystem: Toshiba America Info Systems: Unknown device 0001
	Flags: bus master, slow devsel, latency 168, IRQ 11
GREPping for an inserted PCMCIA modem with filter:        ommunication
 If a PCMCIA modem is currently inserted and the sockets activated by
    /etc/init.d/pcmcia start
 then the PCMCIA bridge is NOT transparent.

 If the modem is known to have a Lucent digital signal processing chipset,
 then PCMCIA.tar.gz variant assembled by Joern Wustenfeld is necessary,
 rather than the standard ltmodem-8.31b1.tar.gz at  http://ltmodem.heby.de/
drwxr-xr-x  2 root root 0 2006-05-18 19:39 /dev/.udevdb

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
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted








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
 Debian  		kernel-headers-2.6.12-9-386    	http://www.debian.org/distrib/packages or install CD
 Ubuntu 		linux-headers-2.6.12-9-386		http://http://packages.ubuntu.com/ or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.12-9-386	   If not present on install CDs search
 	http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/ 
	http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html, or other mirrors.
  SuSE		kernel-source-2.6.12-9-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.12-9-386 or kernel-smp-devel-2.6.12-9-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.12-9-386 proves necessary.
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
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/YourSystem.txt
 ---- dmesg queries -------
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294669.474000] audit: initializing netlink socket (disabled)
[4294709.640000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294709.640000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294723.776000] ibm_acpi: ec object not found
[4294724.082000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[4294724.082000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[4294724.103000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[4294724.103000] toshiba_acpi: ktoshkeyd will check 2 times per second
[4294724.104000] toshiba_acpi: Dropped 0 keys from the queue on startup
[4294740.649000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[4294740.649000] apm: overridden by ACPI.

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the http://www.smlink.com  slmodem software.
  Check pppd version with:
    pppd --version
  See  http://linmodems.technion.ac.il/archive-fourth/msg03167.html
    
  debian_version is not yet providing pre-compiled drivers for WinModems


```

I am obviously running Breezy Badger and would like to get the internet working.
I have used slmodem with wvdial but it always rings out and never dials.

I would appreciate any help so I can stop using Windows all the time.

---

