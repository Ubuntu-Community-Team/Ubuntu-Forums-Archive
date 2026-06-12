---
title: "modem does not work"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by gottfried on 2005-07-13
Hi,
I am using a "Devolo MicroLink 56k Fun USB" modem. It works under SUSE 9.1 with smartlink-softmodem driver, but not under Ubuntu 5.04.
Now I installed
[http://apqi.com/ubuntu/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb](http://apqi.com/ubuntu/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb)
[http://apqi.com/ubuntu/sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb](http://apqi.com/ubuntu/sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb)
My English is not so comfortable, so I can't understand everything my computer is answering.
In the shell I did the following:
cgneumann@ubuntu:~$ cd Desktop/
cgneumann@ubuntu:~/Desktop$ gunzip scanModem.gz
cgneumann@ubuntu:~/Desktop$ chmod +x scanModem
cgneumann@ubuntu:~/Desktop$ sudo ./scanModem
Password:

UPDATE=2005_July_7
ONLY use scanModem downloaded as: 
[http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

./scanModem should ONLY be run within a Linux/UNIX partition.
If within a MicroSoft/DOS partition, abort with Ctrl-C now !!!
Copy scanModem.gz to your Linux partition and restart.

./scanModem: line 265: gcc: command not found


   A subfolder Modem/  has been written,  containing these files with more 
detailed Information:
 ------------------------------------------------------------------------------------------
 1stRead.txt DriverCompiling.txt InfoGeneral.txt ModemData.txt Rational.txt 
Slmodem-ALSA.txt Slmodem.txt Testing.txt UNSUBSCRIBE.txt YourModem.txt
-------------------------------------------------------------------------------------------
       Please read 1stRead.txt first for Guidance.

cgneumann@ubuntu:~/Desktop$ cd Modem
cgneumann@ubuntu:~/Desktop/Modem$ ls
1stRead.txt          ModemData.txt     Slmodem.txt      YourModem.txt
DriverCompiling.txt  Rational.txt      Testing.txt
InfoGeneral.txt      Slmodem-ALSA.txt  UNSUBSCRIBE.txt
cgneumann@ubuntu:~/Desktop/Modem$ cat ModemData.txt


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.04 "Hoary Hedgehog"  kernel 2.6.10-5-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_July_7
------------ --------------  System information ------------------------
 Ubuntu 5.04 "Hoary Hedgehog"
 on System with processor: i686
 currently under kernel:   2.6.10-5-386

There are emerging complications under 2.6.10 and later kernels.  Concerning 
code for:
Smartlink slmodem :
   slmodem-2.9.9d.tar.gz at 
[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
      has the current fixes.  Related messages are:
   [http://www.datiku.com/documents/2610_migration.php](http://www.datiku.com/documents/2610_migration.php)
   [http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html)
   [http://linmodems.technion.ac.il/archive-fourth/msg03736.html](http://linmodems.technion.ac.il/archive-fourth/msg03736.html) .
   [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  has an 
upgrab-winmodem.tar.gz,
       providing a driver to alleviate inappropriate capture of a winmodem by 
a serial port driver.
Lucent/Agere DSP/ltmodem:
  [http://linmodems.technion.ac.il/archive-fourth/msg03733.html](http://linmodems.technion.ac.il/archive-fourth/msg03733.html)
Concerning Intel-536ep and 537
   [http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/](http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/)
   [http://linmodems.technion.ac.il/archive-fifth/msg00280.html](http://linmodems.technion.ac.il/archive-fifth/msg00280.html)
   [http://linmodems.technion.ac.il/archive-fifth/msg00881.html](http://linmodems.technion.ac.il/archive-fifth/msg00881.html)

 The kernel was assembled with compiler:  3.3.5
 a gcc-3.3.5  package must be installed to support driver compiling

A package kernel-kbuild-2.6.3 or later version must be installed to support 
compiling

Checking for kernel-headers needed for compiling.
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!If 
compressed resources are present, expand and then configure them following 
DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and 
mirrows), search for :
  Distribution  PackageName                     OnLine
  ----------------------------------------------------------------------
 Debian                 kernel-headers-2.6.10-5-386     
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu                 linux-headers-2.6.10-5-386              
[http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  
Debian, Ubuntu and Xandros
 Mandrake       kernel-source-2.6.10-5-386         If not present on install 
CDs search
        [http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/)
        [http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or 
other mirrors.
  SuSE          kernel-source-2.6.10-5-386               , kernels are named 
k_deflt
  FedoraCore4  kernel-devel-2.6.10-5-386 or kernel-smp-devel-2.6.10-5-386 on 
install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 
2.6.10-5-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.


Please install the package WVDIAL for modem testing and dialout.

 Modem symbolic link is:  /dev/modem -> ttySL0
 USB modem not detected.

--------- lspci scan ----------------
 PCI_bus
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host 
Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 
Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 
Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 
Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. 
VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. 
VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] 
(rev 74)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY 
[Radeon 7000/VE]
-------------------------------------

 A modem was not detected among the above PCI devices.
 This indicates that the modem, if present has a non-standard or ISA bridge.
 Please follow the directions in Modem/SoftModem.txt  for identifying the 
modem properties
 when booting under Microsoft Windows. Also access any documentation sources
 on yourchipset.  Guidance can only be provided AFTER
 the chipset and/or its drivers have been identified.

 The IBM mwave modem does have a driver within 2.6.n kernel+module releases.  
If is at:
         /lib/modules//kernel/drivers/char/mwave/mwave.ko
and can be loaded only if Mwave hardware is present  Test with:
 #  su - root
 followed by
 # modprobe wmave
 If successful see:
        [http://tedfelix.com/Mwave/](http://tedfelix.com/Mwave/)
        [http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/](http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/)   , section 2.4 and 
later.
        [http://www.freenetpages.co.uk/hp/mjbou/dwtpul.html](http://www.freenetpages.co.uk/hp/mjbou/dwtpul.html)
        [http://tedfelix.com/Mwave/](http://tedfelix.com/Mwave/)

 A failure response has output like:
        FATAL: Error inserting mwave 
(/lib/modules/2.6.10-1-686/kernel/drivers/char/mwave/mwave.ko): Input/output 
error
indicating absence of an Mwave modem

  ======= PCI_ID checking completed ======
 Update=2005_July_7
A PCMCIA CardBus is not detected on this System.
GCCversion=none

For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant 
modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for 
Lucent/Agere DSP modems

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
Be sure to read the section about ppp related modules and aliases in 
Modem/YourModem.txt

  The current modem symbolic link is: /dev/modem -> ttySL0
  The ports /dev/ttyS0 or 1,2,3 are for standard Controller chip modems


 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
audit: initializing netlink socket (disabled)
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.

  Beginning with Fedora 2  kernel-2.6.6-1.427, kernel-headers needed
  for compiling drivers are provide at: /lib/modules/kernel-version/build/
  Thus upgrading above kernel 2.6.5-1.358 to 2.6.6-* is Stongly Recommended

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently 
established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the [http://www.smlink.com](http://www.smlink.com)  slmodem software.
  Check pppd version with:
    pppd --version
  See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)

  debian is not yet providing pre-compiled drivers for WinModems

cgneumann@ubuntu:~/Desktop/Modem$
cgneumann@ubuntu:~/Desktop/Modem$
cgneumann@ubuntu:~/Desktop/Modem$
cgneumann@ubuntu:~/Desktop/Modem$ cd /home/cgneumann
cgneumann@ubuntu:~$ su
Password:
root@ubuntu:/home/cgneumann # slmodemd --c AUSTRIA /dev/slusb0
error: mdm setup: cannot stat `/dev/slusb0': No such file or directoryerror: 
cannot setup device `/dev/slusb0'
root@ubuntu:/home/cgneumann #
root@ubuntu:/home/cgneumann #
root@ubuntu:/home/cgneumann # modprobe ModuleDriver
FATAL: Module ModuleDriver not found.
root@ubuntu:/home/cgneumann # modprobe slusb FATAL: Module slusb not found.
root@ubuntu:/home/cgneumann #

Please can you help me, but please do it step by step because I am a beginner.

Many thanks and greatings from Austria.
Gottfried

---

### Post by varunus on 2005-07-13
Looks to me like you haven't installed your kernel headers or a compiler.  Did you install the packages "build-essential" and "linux-headers-2.6.10-5-386" from synaptic?  If you do this, you should be able to run the installer without errors.  (Change the version on headers if you're using a different version, but that's the one ubuntu comes with.)

Good luck.

---

### Post by gottfried on 2005-07-15
Thank you for your answer. You are right, I installed "build-essential" and "linux-headers-2.6.10-5-386", and the system has changed. It seems that my modem doesn't like me, it works not. Here the shell:

cgneumann@ubuntu:~$ cd Desktop/
cgneumann@ubuntu:~/Desktop$ gunzip scanModem.gz
cgneumann@ubuntu:~/Desktop$ chmod +x scanModem
cgneumann@ubuntu:~/Desktop$ sudo ./scanModem
Password:
Sorry, try again.
Password:

UPDATE=2005_July_7
ONLY use scanModem downloaded as: [http://linmodems.technion.ac.il/packages/scanM](http://linmodems.technion.ac.il/packages/scanM) odem.gz

./scanModem should ONLY be run within a Linux/UNIX partition.
If within a MicroSoft/DOS partition, abort with Ctrl-C now !!!
Copy scanModem.gz to your Linux partition and restart.



   A subfolder Modem/  has been written,  containing these files with more detai led Information:
 ------------------------------------------------------------------------------- -----------
 1stRead.txt DriverCompiling.txt InfoGeneral.txt ModemData.txt Rational.txt Slmo dem-ALSA.txt Slmodem.txt Testing.txt UNSUBSCRIBE.txt YourModem.txt
-------------------------------------------------------------------------------- -----------
       Please read 1stRead.txt first for Guidance.

cgneumann@ubuntu:~/Desktop$ cd Modem
cgneumann@ubuntu:~/Desktop/Modem$ ls
1stRead.txt          ModemData.txt     Slmodem.txt      YourModem.txt
DriverCompiling.txt  Rational.txt      Testing.txt
InfoGeneral.txt      Slmodem-ALSA.txt  UNSUBSCRIBE.txt
cgneumann@ubuntu:~/Desktop/Modem$ cat ModemData.txt


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.04 "Hoary Hedgehog"  kernel 2.6.10-5-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_July_7
------------ --------------  System information ------------------------
 Ubuntu 5.04 "Hoary Hedgehog"
 on System with processor: i686
 currently under kernel:   2.6.10-5-386

There are emerging complications under 2.6.10 and later kernels.  Concerning cod e for:
Smartlink slmodem :
   slmodem-2.9.9d.tar.gz at [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
      has the current fixes.  Related messages are:
   [http://www.datiku.com/documents/2610_migration.php](http://www.datiku.com/documents/2610_migration.php)
   [http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html)
   [http://linmodems.technion.ac.il/archive-fourth/msg03736.html](http://linmodems.technion.ac.il/archive-fourth/msg03736.html) .
   [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  has an upgrab-winmodem.t ar.gz,
       providing a driver to alleviate inappropriate capture of a winmodem by a serial port driver.
Lucent/Agere DSP/ltmodem:
  [http://linmodems.technion.ac.il/archive-fourth/msg03733.html](http://linmodems.technion.ac.il/archive-fourth/msg03733.html)
Concerning Intel-536ep and 537
   [http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/](http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/)
   [http://linmodems.technion.ac.il/archive-fifth/msg00280.html](http://linmodems.technion.ac.il/archive-fifth/msg00280.html)
   [http://linmodems.technion.ac.il/archive-fifth/msg00881.html](http://linmodems.technion.ac.il/archive-fifth/msg00881.html)

 The kernel was assembled with compiler:  3.3.5
 with current System compiler GCC=3.3.5
    /usr/bin/gcc -> gcc-3.3

A package kernel-kbuild-2.6.3 or later version must be installed to support comp iling

Checking for kernel-headers needed for compiling.
The kernel-headers have base folder:
/lib/modules/2.6.10-5-386/build -> /usr/src/linux-headers-2.6.10-5-386
/usr/src/linux-headers-2.6.10-5-386
Please install the package WVDIAL for modem testing and dialout.

 Modem symbolic link is:  /dev/modem -> ttySL0
 USB modem not detected.

--------- lspci scan ----------------
 PCI_bus
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host B ridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Ra deon 7000/VE]
-------------------------------------

 A modem was not detected among the above PCI devices.
 This indicates that the modem, if present has a non-standard or ISA bridge.
 Please follow the directions in Modem/SoftModem.txt  for identifying the modem properties
 when booting under Microsoft Windows. Also access any documentation sources
 on yourchipset.  Guidance can only be provided AFTER
 the chipset and/or its drivers have been identified.

 The IBM mwave modem does have a driver within 2.6.n kernel+module releases.  If  is at:
         /lib/modules//kernel/drivers/char/mwave/mwave.ko
and can be loaded only if Mwave hardware is present  Test with:
 #  su - root
 followed by
 # modprobe wmave
 If successful see:
        [http://tedfelix.com/Mwave/](http://tedfelix.com/Mwave/)
        [http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/](http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/)   , section 2.4 and late r.
        [http://www.freenetpages.co.uk/hp/mjbou/dwtpul.html](http://www.freenetpages.co.uk/hp/mjbou/dwtpul.html)
        [http://tedfelix.com/Mwave/](http://tedfelix.com/Mwave/)

 A failure response has output like:
        FATAL: Error inserting mwave (/lib/modules/2.6.10-1-686/kernel/drivers/c har/mwave/mwave.ko): Input/output error
indicating absence of an Mwave modem

  ======= PCI_ID checking completed ======
 Update=2005_July_7
A PCMCIA CardBus is not detected on this System.
GCCversion=3.3.5

For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant m odems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere  DSP modems

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
Be sure to read the section about ppp related modules and aliases in Modem/YourM odem.txt

  The current modem symbolic link is: /dev/modem -> ttySL0
  The ports /dev/ttyS0 or 1,2,3 are for standard Controller chip modems


 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
audit: initializing netlink socket (disabled)
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
  debian is not yet providing pre-compiled drivers for WinModems


cgneumann@ubuntu:~$ su
Password:
root@ubuntu:/home/cgneumann # dpkg-reconfigure sl-modem-daemon -plow
Shutting down SmartLink Modem driver normally ... no slmodemd daemon running.
Loading ALSA modem driver into kernel ... done.
Starting SmartLink Modem driver for: .
Creating /dev/modem symlink, pointing to: /dev/ttySL0.
root@ubuntu:/home/cgneumann # modprobe ModuleDriver
FATAL: Module ModuleDriver not found.
root@ubuntu:/home/cgneumann # slmodemd --c AUSTRIA /dev/slusb0
error: mdm setup: cannot open dev `/dev/slusb0': No such device or address
error: cannot setup device `/dev/slusb0'

If you know what to do, please tell me.
Many thanks.

---

### Post by sagarhshah on 2006-07-07
hi mate,

I have an "Elsa MicroLink 56k Fun USB" which is the same as your devolo.

I am having pretty much the same problems with my installation of ubuntu as well. Dapper Drake.

Well I have been researching on this for the last 2 weeks and still havent managed to find a solution as yet. Guess I'll have to boot up windows whenever I want to use the internet.

If you do manage to get a workaround please do send us a message.

Thanks

Sagar

---

