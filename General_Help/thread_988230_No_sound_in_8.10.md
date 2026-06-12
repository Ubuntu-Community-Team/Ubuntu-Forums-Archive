---
title: "No sound in 8.10"
date: 2008-11-20
forum: General Help
---

### Post by Toriam on 2008-11-20
My sounds dead. Ive been fooling with it for days with no luck, time to bring in the experts!

Here a shot of alsamixergui and gnome alsa...
And heres  sudo lspci results:

toriam@toriam-laptop:~$ sudo lspci

[sudo] password for toriam: 

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)

02:07.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

02:07.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller

02:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Conrk Connection (rev 05)

toriam@toriam-laptop:~$ 


Pulseaudio is gone.
Everythings alsa.
Sound doesn't work at all.
I have a weird thing from when I was running inferior software where I unUSBed without clicking and it killed sound and my inverter board. But under Kubuntu my magical boyfriend wiggled the settings and got it to work. 
I got a little sound at one time but now.. nothing. 
Is there any way to activate slider bars (not just on mute, no bar) in alsa?

---

### Post by Toriam on 2008-11-27
Bump!

---

### Post by ravalox on 2008-11-29
Bump!  Also this is kind of ridiculous.

---

