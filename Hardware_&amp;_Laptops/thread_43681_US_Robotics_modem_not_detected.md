---
title: "US Robotics modem not detected"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by Jenda on 2005-06-22
Hello, forums.

I am trying to configure Ubuntu for my aunt. The computer has a U.S. Robotics 56K fax PCI modem on COM 3. I tried setting it up through pppconfig and administration>networking, but neither worked.

Other data I found out in Windows is: PCI Slot 4 (PCI bus 0, device 9, function 0)

Can anyone help me, please?

---

### Post by az on 2005-06-22
If it is a software modem, it does not work in linux.  USRobotics make great hardware modems, but they refuse to support linux.

Use scanmodem
[https://wiki.ubuntu.com/forum/hardware/modem](https://wiki.ubuntu.com/forum/hardware/modem)
[https://wiki.ubuntu.com/forum/hardware/](https://wiki.ubuntu.com/forum/hardware/)

---

### Post by Jenda on 2005-06-23
Okay... bad news. No internet, then.

---

### Post by Jenda on 2005-06-23
OK... scanModem's ModemData contains:

> :~/Desktop/Modem$ cat ModemData.txt


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.04 "Hoary Hedgehog"  kernel 2.6.10-5-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_June_21
------------ --------------  System information ------------------------
 Ubuntu 5.04 "Hoary Hedgehog"
 on System with processor: i686
 currently under kernel:   2.6.10-5-386

There are emerging complications under 2.6.10 and later kernels.  Concerning code for:
Smartlink slmodem :
   slmodem-2.9.9d.tar.gz at [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
      has the current fixes.  Related messages are:
   [http://www.datiku.com/documents/2610_migration.php](http://www.datiku.com/documents/2610_migration.php)
   [http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html)
   [http://linmodems.technion.ac.il/archive-fourth/msg03736.html](http://linmodems.technion.ac.il/archive-fourth/msg03736.html) .
   [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  has an upgrab-winmodem.tar.gz,
       providing a driver to alleviate inappropriate capture of a winmodem by a serial port driver.
Lucent/Agere DSP/ltmodem:
  [http://linmodems.technion.ac.il/archive-fourth/msg03733.html](http://linmodems.technion.ac.il/archive-fourth/msg03733.html)
Concerning Intel-536ep and 537
   [http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/](http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/)
   [http://linmodems.technion.ac.il/archive-fifth/msg00280.html](http://linmodems.technion.ac.il/archive-fifth/msg00280.html)
   [http://linmodems.technion.ac.il/archive-fifth/msg00881.html](http://linmodems.technion.ac.il/archive-fifth/msg00881.html)

 The kernel was assembled with compiler:  3.3.5
 a gcc-3.3  package must be installed to support driver compiling

A package kernel-kbuild-3.6 or later version must be installed to support compiling

Checking for kernel-headers needed for compiling.
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName                     OnLine
  ----------------------------------------------------------------------
 Debian                 kernel-headers-2.6.10-5-386     [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu                 linux-headers-2.6.10-5-386              [http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake       kernel-source-2.6.10-5-386         If not present on install CDs search
        [http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/)
        [http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE          kernel-source-2.6.10-5-386               , kernels are named k_deflt
One of which must be installed if compiling drivers to match kernel 2.6.10-5-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.


Please install the package WVDIAL for modem testing and dialout.

 A /dev/modem symbolic link is not set.
 USB modem not detected.

0000:00:0b.0 Multimedia audio controller: Aureal Semiconductor AU8810 Vortex Digital Audio Processor (rev 02)

Modem candidates are at PCI_buses:  0000:00:09.0

Providing detail for device at  0000:00:09.0
  with vendor-ID:device-ID
            ----:----
Class 0700: 12b9:1008   Serial controller: 5610 56K FaxModem 56K FaxModem Model 5610 (rev 01) (prog-if 02 [16550])
  SubSystem 12b9:00ad   5610 56K FaxModem USR 56k Internal FAX Modem (Model 5610)
0000:00:09.0 0700: 12b9:1008 (rev 01) (prog-if 02)
        Flags: medium devsel, IRQ 11

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 12b9:1008 12b9:00ad debian 2.6.10-5-386  3.3.5 none    i686


 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.

 == Checking PCI IDs through modem chip suppliers ==

 10b7 is 3COM
       :1006    0038TA <- AC101 - TF Mini-PCI 56K V.90 WinModem  no Linux support
       :1007    3C556 V.90 Mini-PCI     WinModem  no Linux support
 12b9 is US Robotics. acquired by 3COM
       :0062    erk41926a-0.6 usr 56k internal modem
       ;1006    3cp803598  Voice          WinModem  no Linux support
       :1007    ERL3263A-0 DF GWPCI PC99  WinModem  no Linux support
       :1008    3cp803598  is Supported by the standard:  serial.o
 The following may be supported  by Conexant drivers at   [http://www.linuxant.com](http://www.linuxant.com)
   14f1:2f12 (3COM/USR model 3094-3095)
   14f1:2f13 (USR OEM)
   14f1:2f14 3COM/USR
 though they carry USR labels.


  ======= PCI_ID checking completed ======
 Update=2005_June_21
A PCMCIA CardBus is not detected on this System.
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
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/YourModem.txt
DEVPPP=crw-rw---- 1 root root 108, 0 2005-06-23 12:41 /dev/ppp
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
Local APIC disabled by BIOS -- you can enable it with "lapic"
CPU serial number disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
audit: initializing netlink socket (disabled)
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
  debian is not yet providing pre-compiled drivers for WinModems

Does this tell you if it's a HW or SW modem, and if it can be used under Linux?

Thanks for your help,

Jenda

---

### Post by Mr. Shifty on 2006-06-03
I believe I have the same problem.... I'm not that great with Linux yet and have no clue what process it takes to get this working.... and it sounds like i have the same or a similar modem as jenda

---

### Post by Jenda on 2006-06-05
Hmm.. I don't have the modem anymore - nor do I remember how/if I solved the problem :( sorry.

---

### Post by Mr. Shifty on 2006-06-05
ok, thanks anyways

---

