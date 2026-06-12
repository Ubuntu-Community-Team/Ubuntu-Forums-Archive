---
title: "Can't install Best Data 56USBP usb hardware modem"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by ry_ry on 2005-07-29
I have a Best Data 56USBP usb modem and Ubuntu doesn't see it at all. It is a hardware modem. It worked just fine under SimplyMepis, and others have said that it worked under Mandrake and Red Hat. So why can't Ubuntu see it. I tried pppconfig, and gnome-ppp. And the networking option as well. Under Mepis it was on /dev/ttyACM0 but under Ubuntu 5.04 there are no ACM's to choose from. I always get no modem attached error messages. The usb modem shows up in Device Manager in Ubuntu.

After lsusb it shows:
Bus 001 Device 003: ID 05 72:280 Conexant Systems (Rockwell), Inc.

When I unplug and replug it back in, dmesg shows at the end:
USB 1-1.3: USB disconnect, address 3
USB 1-1.3: New full speed USB device using uhci_hcd and address 4
cdc_acm: probe of 1-1.3:1.1 failed with error -16

I ran scanmodem and it shows below:


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
S:  Product=USB ACF Modem

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



I tried to follow the wiki about installing the Intel 536ep but that didn't work.
I tried installing both HCF and HSF drivers from linuxant.com/drivers but that didn't work.

I didn't have to install any drivers under Mepis for it to work. Why doesn't Ubuntu have any ACM devices listed in gnome-ppp to choose from? Am I missing something? I'm still a newb, but this installing a usb modem has been a real pain. This usb modem works with a Mac also.

So any ideas on how to get Ubuntu to use this hardware modem?
If I can't get it to work in Ubuntu, then I'll have to try a different Linux distro., since I know that Mandrake, Red Hat and Mepis can install this modem with no problems.

Any help would be great!
Thank you.

---

### Post by greenfrog on 2005-09-13
Do modprobe cdc-acm, that will install the acm driver and you should be able to then use the modem at /dev/ttyACM0

That is what I had to do to get it to work, now if I cound just get it to work the the Gnome dialer

---

