---
title: "modem and web"
date: 2005-03-04
forum: Hardware &amp; Laptops
---

### Post by LK_gandalf_ on 2005-03-04
Hi, i'd like to know how to verify if an internal modem 56k is correctly known by ubunt and then how to make a simple analogic connection to internet.

I have an acer1522wlmi, and I'm a newbies of linux. 

thanks

---

### Post by az on 2005-03-04
[http://linmodems.technion.ac.il/#scanmodem](http://linmodems.technion.ac.il/#scanmodem)

Use that to check your hardware.

Post the output here if you do not know where to go from there.

---

### Post by LK_gandalf_ on 2005-03-13
Hi, I did the scan and now i have a directory called Modem. I read I have to post te file Modemdata.txt, here the response! I don't know how to go on....thank you very much 

DO use the following line as the email Subject Line, to alert cogent experts:
scanModem, Ubuntu 4.10 kernel 2.6.8.1-3-386
Occassionally reponses are blocked by an Internet Providers mail filters.
So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]

Code updated on:  2005_March_3
------------ --------------  System information ------------------------
Ubuntu 4.10 "Warty Warthog" 
 on System with processor: i686
 currently under kernel:   2.6.8.1-3-386
 The kernel was assembled with compiler:  3.3.4
 with current System compiler GCC=3.3.4
    /usr/bin/gcc -> gcc-3.3

Checking for kernel-headers needed for compiling.
Kernel-header resources are not evident.
Within your Linux distributions resources, search for package names with:
  linux-headers-2.6.8.1-3-386
  kernel-source-2.6.8.1-3-386
  linux-2.6.8.1-3-386
One of which must be installed if compiling drivers to match kernel 2.6.8.1-3-386 proves necessary.
This is necessary for most modem drivers, through some Linux distributions provide some compiled drivers.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
  

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  0000:00:11.6
    
Providing detail for device at PCI_bus 0000:00:11.6
  with vendor-ID:device-ID
	    ----:----
Class 0780: 1106:3068   Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Modem] (rev 80)
  SubSystem 1025:0046   Acer Incorporated [ALI]: Unknown device 0046
	Flags: medium devsel, IRQ 201
	I/O ports at 1800
	Capabilities: [d0] Power Management version 2
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 1106:3068 1025:0046 debian 2.6.8.1-3-386 3.3.4 3.3.4    i686

       
 The soft modem Subsystem operates under a controller
   1106:3068  VIA 
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:

	Pctel
	AgereSystems
	Conexant
	Intel
	Smartlink
 The Subsystem PCI id does not itself identify the modem Codec.
  Driver snd-intel8x0m  may enable codec acquisition 

 Beginning check for older ac97_codec modems.
 An older ac97_modem codec was not detected.

 Checking through information gathered from LinModem ARCHIVES
 From prior reports, the modem codec type of the Subsystem is: SIL27
 The Subsystem has an Agere Systens codec SIL27
 SmartLink software should support this modem
	Due to a PCI ID database error, the Intel 537 designation is commonly incorrect.
 == Checking PCI IDs through modem chip suppliers ==

 Vendor=1025 is Acer, [http://global.acer.com/](http://global.acer.com/) PC and latop manufacturer with devices including:
  1025:5453   M5453 AC-Link Controller Modem Device
  1025:0038   an AC97 link modem.


 Under the controller 1106:3068  VIA ,
 with modem subSystem 1025:0046     
 Alternative supporting packages are the SmartLink slmodem-2.9.N using its proprietary slamr driver, 
 OR the Open Source snd-intel8x0m.ko driver included with recent 2.6.n kernel installations,
    complemented by the daemon, slmodemd,  of the slmodem-2.9.9-alsa.tar.gz package available at:
            [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
    A major advantage is that driver compiling is not necessary upon kernel updates
.  The command sequence is:
    # modprobe snd-intel8x0m
    # slmodemd --alsa --country=YOURCOUNTRY hw:0 
   with the slmodemd providing for dynamic port creation:
         /dev/ttySL0 --> /dev/pts/N    
   and higher level functions.
 Read the slmodem package readme, Modem/Slmodem.txt and Modem/SoftModem.txt for details.
 
 For SuSE 9.2 users, there is an update  for driver slamr.ko loading during bootup. 
 To find it easily, search for "slamr" within  [http://www.novell.com/linux/download/updates/92_i386.html](http://www.novell.com/linux/download/updates/92_i386.html)
     

 SmartLink at [http://www.smlink.com/](http://www.smlink.com/) owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40) ,
  but [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) has older packages and new fixes.
      For the emerging 2.6.10 kernels, use the slmodem-2.9.9a.tar.gz  therefrom.
 Read Slmodem.txt  for details.
   
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 1106 is VIA  Technologies Inc.,producing diverse bridges including devices:
    1106:3068    VT82C686/686A/686B AC97 Modem Codec
 Under the later, the  10cf:118e  the "Intel 537" is partially supported
   by the SmartLink slmodem-2.7.10 software
    Subsystem 1102:0033 has an AgereSystems soft modem chip


  ======= PCI_ID checking completed ====== 
 Update=2005_March_3

Analyzing information for PCMCIA device at PCI Bus 00:0b.0
GREPping for an inserted PCMCIA modem with filter:        ommunication

Analyzing information for PCMCIA device at PCI Bus 00:0b.1
GREPping for an inserted PCMCIA modem with filter:        ommunication
 A PCMCIA modem is detected.
      
 The stardard ltmodem resources should suffice for modem support:
     [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
 if the modem has a Lucent/Agere digital processing chipset.
 
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias char-major-108 ppp_generic
/etc/modprobe.d/aliases:alias tty-ldisc-3  ppp_async  
/etc/modprobe.d/aliases:alias tty-ldisc-14 ppp_synctty
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe
/etc/modprobe.d/aliases:alias ppp-compress-21 bsd_comp   
/etc/modprobe.d/aliases:alias ppp-compress-24 ppp_deflate
/etc/modprobe.d/aliases:alias ppp-compress-26 ppp_deflate
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/General.txt

  A port needed for the PPP protocol is absent!!!
  echo "  crw-------    1 root     root     108,   0 Dec 31  1969 /dev/ppp"

A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *11, disabled.
ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *11, disabled.

  There are Debian packages with modem drivers from SmartLink:
      sl-modem-daemon - SmartLink software modem daemon
      sl-modem-source - SmartLink software modem driver - module building source
  MANY modem subSystems serving under AC97/MC97 Controllers are also supported.

---

### Post by az on 2005-03-13
There are packages in multiverse called sl-modem-daemon and sl-modem-source.

Try just installing the sl-modem-daemon.  It can use an alsa module that is already present on your system.

If that fails (read the docs, first)  install sl-modem-source, build-essential and linux-headers and build the proprietary driver.

---

### Post by LK_gandalf_ on 2005-03-14
[QUOTE=azz]There are packages in multiverse called sl-modem-daemon and sl-modem-source.

Try just installing the sl-modem-daemon.  It can use an alsa module that is already present on your system.[/QUOTE]

Sorry i'm completely newbie  ](*,) , what is sl-modem-daemon I have to install? I have to download it? 

thank you

---

