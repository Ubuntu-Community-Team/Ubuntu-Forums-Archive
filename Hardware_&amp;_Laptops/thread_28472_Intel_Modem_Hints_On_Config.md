---
title: "Intel Modem Hints On Config??"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by JacX on 2005-04-20
Hi

Does anyone haveany ideas on how to configure an Intel modem as Hoary didn't want to play when I installed last night??

Have had a scan of the site but if anyone could point me in the direction of a Howto or site it would be really appreciated.

---

### Post by brk3 on 2005-04-20
What exactly do you mean when you say it didnt want to play..?
Kppp should cater for all your configurtions.  ;-)

---

### Post by JacX on 2005-04-20
Forgive me but I thought KPPP was to configure a dial up account and used to connect.  My modem is not reconised by the system so I thought I would be able to manually configure it?!?!?

---

### Post by speedman on 2005-04-20
You will have to precisely identify the chipset on your modem before determining what drivers may, or may not be available for it.

Post the output of lspci, which should reveal the pertinent details.


Regards,

SM

---

### Post by JacX on 2005-04-21
I would if I had any idea what ISPCI is!?!?!?   :-? 

Is there a tool I could download and run to identify the chipset??

---

### Post by speedman on 2005-04-21
Right click on the desktop "Open Terminal.  Type the command lspci in the terminal, hit enter and copy and paste the output specific to your modem here and somebody will help you identify the chipset.


Regards,

SM

---

### Post by wizer on 2005-07-20
Hi Speedman
I am new to Linux.  I am facing the same problem on my Fujitsu S7021 (uses Agere System HDA Modem according to XP).

I have tried to type Ispci on both my user terminal & the root terminal but I get the following error message from bash:
  lspci: command not found

Do I have to install something first?

Thanks for your help.

---

### Post by kafton on 2005-07-20
Go to [http://linmodems.org/](http://linmodems.org/) . Download the scanModem tool and run it to find out which chipset your modem has. Go get the appropriate driver.

---

### Post by wizer on 2005-07-21
Hi Kafton
I have run scanModem but I dont know where to find in ModemData.txt my chipset.  Can you help me? I am including below the contents of the file.


beg of file

 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.04 "Hoary Hedgehog"  kernel 2.6.10-5-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_July_19
------------ --------------  System information ------------------------
 Ubuntu 5.04 "Hoary Hedgehog" 
 on System with processor: i686
 currently under kernel:   2.6.10-5-386

There are emerging complications under 2.6.10 and later kernels. 
Concerning Intel-536ep and 537
   [http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/](http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/) 
   [http://linmodems.technion.ac.il/archive-fifth/msg00280.html](http://linmodems.technion.ac.il/archive-fifth/msg00280.html)
   [http://linmodems.technion.ac.il/archive-fifth/msg00881.html](http://linmodems.technion.ac.il/archive-fifth/msg00881.html)
   
 The kernel was assembled with compiler:  3.3.5
 a gcc-3.3.5  package must be installed to support driver compiling

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling

Checking for kernel-headers needed for compiling.
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName   OnLine
  ----------------------------------------------------------------------
 Debian    kernel-headers-2.6.10-5-386     [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu   linux-headers-2.6.10-5-386  [http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake  kernel-source-2.6.10-5-386    If not present on install CDs search
  [http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
 [http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE  kernel-source-2.6.10-5-386   , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.10-5-386 or kernel-smp-devel-2.6.10-5-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.10-5-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

Please install the package WVDIAL for modem testing and dialout.

 A /dev/modem symbolic link is not set.
 USB modem not detected.

--------- lspci scan ----------------
 PCI_bus
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:02:00.0 Ethernet controller: Broadcom Corporation: Unknown device 167d (rev 11)
0000:06:03.0 CardBus bridge: O2 Micro, Inc.: Unknown device 7134 (rev 20)
0000:06:03.2 0805: O2 Micro, Inc.: Unknown device 7120
0000:06:03.3 Bridge: O2 Micro, Inc.: Unknown device 7130
0000:06:05.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:06:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
-------------------------------------

 A modem was not detected among the above PCI devices.
 This indicates that the modem, if present has a non-standard or ISA bridge.
 Please follow the directions in Modem/SoftModem.txt  for identifying the modem properties
 when booting under Microsoft Windows. Also access any documentation sources
 on yourchipset.  Guidance can only be provided AFTER
 the chipset and/or its drivers have been identified.
 
 The IBM mwave modem does have a driver within 2.6.n kernel+module releases.  If is at:
   /lib/modules/2.6.10-5-386/kernel/drivers/char/mwave/mwave.ko
and can be loaded only if Mwave hardware is present  Test with: 
 #  su - root
 followed by
 # modprobe wmave
 If successful see: 
  [http://tedfelix.com/Mwave/](http://tedfelix.com/Mwave/)
  [http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/](http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/)   , section 2.4 and later.
  [http://www.freenetpages.co.uk/hp/mjbou/dwtpul.html](http://www.freenetpages.co.uk/hp/mjbou/dwtpul.html)
 [http://tedfelix.com/Mwave/](http://tedfelix.com/Mwave/)
 
 A failure response has output like:
  FATAL: Error inserting mwave (/lib/modules/2.6.10-1-686/kernel/drivers/char/mwave/mwave.ko): Input/output error
indicating absence of an Mwave modem

  ======= PCI_ID checking completed ====== 
 Update=2005_July_19

Analyzing information for PCMCIA device at PCI Bus 06:03.0
0000:06:03.0 CardBus bridge: O2 Micro, Inc.: Unknown device 7134 (rev 20)
 Subsystem: Fujitsu Limited.: Unknown device 131e
 Flags: bus master, stepping, slow devsel, latency 168, IRQ 16
 Memory at 30080000 (32-bit, non-prefetchable) [size=4K]
 Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
 Memory window 0: 30400000-307ff000 (prefetchable)
 Memory window 1: 30800000-30bff000
 I/O window 0: 00004000-000040ff
 I/O window 1: 00004400-000044ff
 16-bit legacy interface ports at 0001

GREPping for an inserted PCMCIA modem with filter:        ommunication
 If a PCMCIA modem is currently inserted and the sockets activated by
    /etc/init.d/pcmcia start
 then the PCMCIA bridge is NOT transparent.

 If the modem is known to have a Lucent digital signal processing chipset,
 then PCMCIA.tar.gz variant assembled by Joern Wustenfeld is necessary,
 rather than the standard ltmodem-8.31a10.tar.gz at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
GCCversion=none
   
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
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:12:F0:70:30:9B  
          inet6 addr: fe80::212:f0ff:fe70:309b/64 Scope:Link
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/YourModem.txt
 Be sure to read the Ethernet section of Modem/YourModem.txt 
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
audit: initializing netlink socket (disabled)
ibm_acpi: ec object not found
apm: BIOS not found.

  Beginning with Fedora 2  kernel-2.6.6-1.427, kernel-headers needed 
  for compiling drivers are provide at: /lib/modules/kernel-version/build/
  Thus upgrading above kernel 2.6.5-1.358 to 2.6.6-* is Stongly Recommended
  
  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the [http://www.smlink.com](http://www.smlink.com)  slmodem software.
  Check pppd version with:
    pppd --version
  See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)
    
  debian is not yet providing pre-compiled drivers for WinModems

end of file

---

