---
title: "Local HP LaserJet 1000 won't print"
date: 2008-11-11
forum: Hardware
---

### Post by SemperMollis on 2008-11-11
Hello. I'm new to Linux (<48 hrs.) and I could use some help.

I've just installed:

Ubuntu release 8.10 (intrepid)
Kernel Linux 2.6.27-7-generic
GNOME 2.24.1

On a Dell 530S with an Intel Pentium Dual-Core CPU E2160 @ 1.8 GHz
ATI Radeon HD 2400 PRO running ATI/AMD proprietary FGLRX graphics driver
2 gb RAM

This is a dual boot machine with XP Pro sp3.

The following drivers were automatically installed:

hplip 2.8.7-0ubuntu6
hpijs 2.8.7-0ubuntu6
hplip-data 2.8.7-0ubuntu6
pxljr 1.1-0ubuntu3

This is a local USB printer. The system recognized and installed it automatically. When I send a print job or test page to it, it shows completed but does not print. The printer works fine on this machine booted into WinXP. It also works fine as a Windows networked printer.

I downloaded and installed 2.8.10.  I got an error during the install that the required plug-in failed to install. I tried to download and install the plug-in manually from the HP Device Manager and received this error: Plug-in download failed.

I ran the "hp-check" utility (hp-check -t) and had 1 error/warning:

Under: INSTALLED CUPS PRINTER QUEUES
 
hp-LaserJet-1000
----------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/hp_LaserJet_1000?serial=0
PPD: /etc/cups/ppd/hp-LaserJet-1000.ppd
PPD Description: HP LaserJet 1000 Foomatic/foo2zjs (recommended)
Printer status: printer hp-LaserJet-1000 is idle.  enabled since Tue 11 Nov 2008 11:39:21 AM EST
error: Required plug-in status: Not installed
Communication status: Good

Can anyone tell me where to get a copy of the required plug-in or advise me how to proceed further?

Is there some additional configuration needed? 

Thank you in advance for your answers.

---

### Post by OJX on 2009-02-08
> **SemperMollis said:**
> Hello. I'm new to Linux (<48 hrs.) and I could use some help.

I've just installed:

Ubuntu release 8.10 (intrepid)
Kernel Linux 2.6.27-7-generic
GNOME 2.24.1

On a Dell 530S with an Intel Pentium Dual-Core CPU E2160 @ 1.8 GHz
ATI Radeon HD 2400 PRO running ATI/AMD proprietary FGLRX graphics driver
2 gb RAM

This is a dual boot machine with XP Pro sp3.

The following drivers were automatically installed:

hplip 2.8.7-0ubuntu6
hpijs 2.8.7-0ubuntu6
hplip-data 2.8.7-0ubuntu6
pxljr 1.1-0ubuntu3

This is a local USB printer. The system recognized and installed it automatically. When I send a print job or test page to it, it shows completed but does not print. The printer works fine on this machine booted into WinXP. It also works fine as a Windows networked printer.

I downloaded and installed 2.8.10.  I got an error during the install that the required plug-in failed to install. I tried to download and install the plug-in manually from the HP Device Manager and received this error: Plug-in download failed.

I ran the "hp-check" utility (hp-check -t) and had 1 error/warning:

Under: INSTALLED CUPS PRINTER QUEUES
 
hp-LaserJet-1000
----------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/hp_LaserJet_1000?serial=0
PPD: /etc/cups/ppd/hp-LaserJet-1000.ppd
PPD Description: HP LaserJet 1000 Foomatic/foo2zjs (recommended)
Printer status: printer hp-LaserJet-1000 is idle.  enabled since Tue 11 Nov 2008 11:39:21 AM EST
error: Required plug-in status: Not installed
Communication status: Good

Can anyone tell me where to get a copy of the required plug-in or advise me how to proceed further?

Is there some additional configuration needed? 

Thank you in advance for your answers.

I'm running ubuntu 8.10 on the eee pc and the same printer is recognized but when I try to print, it pretends to print but nothing happens.

---

