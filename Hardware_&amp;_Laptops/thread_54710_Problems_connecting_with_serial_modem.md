---
title: "Problems connecting with serial modem"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by ry_ry on 2005-08-05
Ok, I just bought a Diamond SupraExpress 56e Pro serial modem and this is the first time I'm using it. I hooked it up using a USB to Serial cable. If I use pppconfig to setup the connection, it will dial in and connect but Firefox can't seem to see the internet. So I tried gnome-ppp. Gnome-ppp will auto-detect the modem and that seems fine but when after it dials into my ISP, it keeps dropping the connection, something about the carrier line. But if I use the Networking setup, I can dial in and connect but I would rather use gnome-ppp. Why doesn't gnome-ppp stay connected and why doesn't pppconfig work either?

---

### Post by ry_ry on 2005-08-05
well now I've managed to get pppconfig to work and Firefox can see the internet. I setup the Network connection then I ran pppconfig and it seems like both work now, but gnome-ppp still doesn't work. This doesn't make sense. Gnome-ppp will autodetect the modem on /dev/ttyUSB0 and you can even see the modem lights come on. It will dial out and just when you're suppose to connect, the modem hangs up and the log says something about carrier line. Is there any way to fix this? Why is this acting so weird?

CONNECT 115200
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...

It does this over and over whenever I try to use gnome-ppp. Any ideas?  ](*,)

---

### Post by ry_ry on 2005-08-05
the mystery goes on. Well, I took off the usb to serial adapter. Plug the serial modem straight into the serial port and then booted up Ubuntu. I tried gnome-ppp again and autodetected my serial modem on /dev/ttyS2. It dialed out and connected and then hung up as usual. The log showed exactly what was shown above. So it's not a usb problem, or a usb to serial adapter problem. It seems like gnome-ppp is having a problem staying connected with this serial modem, but why? pppconfig works, and networking works. So why can't gnome-ppp work? Do I need to insert a init. string?

Any suggestions? Should I reinstall from scatch and start all over again?

---

### Post by ry_ry on 2005-08-05
here's a copy of scanModem with the Diamond SupraExpress 56e PRO hooked up to the serial port. The modem is not listed in Device Manager in Ubuntu either.



 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.04 "Hoary Hedgehog"  kernel 2.6.10-5-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_July_21
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
 with current System compiler GCC=3.3.5
    /usr/bin/gcc -> gcc-3.3

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling

Checking for kernel-headers needed for compiling.
The kernel-headers have base folder: 
/lib/modules/2.6.10-5-386/build -> /usr/src/linux-headers-2.6.10-5-386
/usr/src/linux-headers-2.6.10-5-386
Please install the package WVDIAL for modem testing and dialout.

 A /dev/modem symbolic link is not set.
 USB modem not detected.

--------- lspci scan ----------------
 PCI_bus
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0d.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:00:0e.0 Multimedia video controller: Zoran Corporation ZR36120 (rev 03)
0000:00:10.0 Multimedia audio controller: Aureal Semiconductor Vortex 1 (rev 02)
0000:01:00.0 VGA compatible controller: NVidia / SGS Thomson (Joint Venture) Riva128 (rev 21)
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
 Update=2005_July_21
A PCMCIA CardBus is not detected on this System.
GCCversion=3.3.5
   
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
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
Local APIC disabled by BIOS -- you can enable it with "lapic"
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
audit: initializing netlink socket (disabled)
hda: Host Protected Area disabled.
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
  debian is not yet providing pre-compiled drivers for WinModems


I thought serial modems were suppose to be a snap to install in Linux?
The game is afoot.

---

### Post by ry_ry on 2005-08-06
Well, I did a test. I booted the LiveCD, and then installed gnome-ppp in the LiveCD session. Again gnome-ppp would not hold a connection with my serial modem, but pppconfig and network could. So I guess unless someone has an explaination for this, then I'll have to use pppconfig to use my serial modem. I would rather use gnome-ppp for it's UI, but for some reason it just won't work. I'll keep playing around with it. Maybe I'll figure out why gnome-ppp won't work. Any ideas would be welcomed.

---

### Post by ry_ry on 2005-08-06
YES! I fixed it!! I tried to use wvdial and was getting the same error. So I tried "Check carrier = no" in wvdial.conf and then it worked. So I then loaded up gnome-ppp and unchecked "Check carrier" in the modem setup and tried it and it worked!    :grin: 
So if anyone else has this problem, try this and see if it helps you.  ;-)

---

