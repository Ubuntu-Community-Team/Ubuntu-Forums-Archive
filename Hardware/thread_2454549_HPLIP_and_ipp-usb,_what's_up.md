---
title: "HPLIP and ipp-usb, what's up????"
date: 2020-12-01
forum: Hardware
---

### Post by mocha on 2020-12-01
Something curious I noticed after upgrading 19.10 to 20.04 and then again from 20.04 to 20.10.  There seems to be a sea-change in terms of how USB printers are handled in Ubuntu and maybe Linux in general.  I've tended to own HP printers primarily for their support in Linux via the HPLIP package.  That package always did a great job of supporting all the specialized features of the multi-function printers very well, e.g. optical disc printing, various tray selections, photo printing, glossy paper support, ink level reporting, head cleaning, cartridge alignment, test pages, etc...

When I updated to 20.04 the first thing I noticed is that the hp-systray utility could no longer see my printer.  Long story short, I found out that a package called "ippusbxd" got installed during the update and took over the driver functions for my printer.  Same thing happened when I updated to 20.10, except a newer package called "ipp-usb" got installed and basically did the same thing.

Is the intention to deprecate vendor specific driver and supporting software for printers under Linux?  How does making USB printers look like network printers help us end-users in terms of special support that tends to only show up in the specific driver packages?  I'm fearful of losing functionality.  Maybe this is unfounded but right now I don't understand how a generic driver is supposed to support all those special features found on the various models.

I found various links and discussions about these changes but not in terms of my concerns.

[https://wiki.debian.org/CUPSDriverlessPrinting]("https://wiki.debian.org/CUPSDriverlessPrinting")

[https://bugs.launchpad.net/ubuntu/+source/ipp-usb/+bug/1891157]("https://bugs.launchpad.net/ubuntu/+source/ipp-usb/+bug/1891157")

---

### Post by oldfred on 2020-12-01
[https://www.pwg.org/ipp/everywhere.html](https://www.pwg.org/ipp/everywhere.html)

It is my understanding that Linux is finally using the built in drivers that Macs & Windows use.


Driverless printing support is now available. 
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)

---

### Post by brian_p on 2020-12-02
> **mocha said:**
> 
Is the intention to deprecate vendor specific driver and supporting software for printers under Linux?  How does making USB printers look like network printers help us end-users in terms of special support that tends to only show up in the specific driver packages?  I'm fearful of losing functionality.  Maybe this is unfounded but right now I don't understand how a generic driver is supposed to support all those special features found on the various models.

The intention is make printer installation as easy and effortless as plugging in a mouse by leveraging the changes in modern printer technology. AFAIK, all the features of an MFD are discovered and presented by CUPS/cups-filters from querying the printer or via the printer's web interface.

ipp-usb has replaced ippusbxd because it does a much better job. Turning a USB connected device into a network device makes it possible to discover and support the device's attributes via IPP.

---

### Post by mocha on 2020-12-04
> **brian_p said:**
> The intention is make printer installation as easy and effortless as plugging in a mouse by leveraging the changes in modern printer technology. AFAIK, all the features of an MFD are discovered and presented by CUPS/cups-filters from querying the printer or via the printer's web interface.

ipp-usb has replaced ippusbxd because it does a much better job. Turning a USB connected device into a network device makes it possible to discover and support the device's attributes via IPP.

But how does this work?  Even in Windows you need to load the OEM's driver software to reveal functions that are specific to a particular printer.  I thought this was the intention of software such as HPLIP.  How can CUPS contain all of the "stuff" that is included with HPLIP as well as every other printer manufacturer?  For example, a number of years back if you had an HP MFD we had the option of loading the gutenprint packages and plugins, or we could load HPLIP.  If you loaded gutenprint, it worked fairly well for basic letter size and photos.  But if you wanted to use the optical disc printer tray or other special functions then you had to use HPLIP.

---

### Post by brian_p on 2020-12-04
> **mocha said:**
> But how does this work?  Even in Windows you need to load the OEM's driver software to reveal functions that are specific to a particular printer.  I thought this was the intention of software such as HPLIP.  How can CUPS contain all of the "stuff" that is included with HPLIP as well as every other printer manufacturer?  For example, a number of years back if you had an HP MFD we had the option of loading the gutenprint packages and plugins, or we could load HPLIP.  If you loaded gutenprint, it worked fairly well for basic letter size and photos.  But if you wanted to use the optical disc printer tray or other special functions then you had to use HPLIP.

Practically every printer sold in the past five to eight years uses the IPP protocol. All major vendors have standardised on this protocol and employ it via their devices' firmware. From that point of view, all printer manufacturers are the same (barring any buggy firmware). HP cannot claim that its version of IPP is better than Brother's, provided both have diligently implemented what the is printer capable of in the firmware. The printing system can discover what the firmware offers in terms of print quality, paper type, media size, trays etc.

Almost every printer sold in the past five to eight years offers AirPrint. AirPrint certification from Apple requires the printer to accept Apple raster. CUPS+cups-filters hasn't any problem producing and sending Apple raster. From that point of view, all printer manufacturers use a common printer language. Epson cannot claim that its version of Airprint is better than Canon's.

In the example you give, different drivers are involved. Gutenprint had probably not figured out how to print satisfactorily on a DVD, whereas HP had the edge. Nowadays, a user does not need to change drivers when using a different printer.

---

### Post by mocha on 2020-12-05
Thanks for the info.  I'm actually getting convinced to try it out.  Is it as simple as installing ipp-usb and then creating a printer within the cups interface or the DE tools?  I use XFCE primarily.  Can I try it out without removing HPLIP in case I don't want to mess everything up?

---

### Post by brian_p on 2020-12-05
> **mocha said:**
> Thanks for the info.  I'm actually getting convinced to try it out.  Is it as simple as installing ipp-usb and then creating a printer within the cups interface or the DE tools?  I use XFCE primarily.  Can I try it out without removing HPLIP in case I don't want to mess everything up?

Yes, it's as simple as that. Actually, the print queue should be auto-created by cups-browsed when the printer is plugged in. HPLIP can be left on the system.

What is your device model?

---

### Post by mocha on 2020-12-05
> **brian_p said:**
> Yes, it's as simple as that. Actually, the print queue should be auto-created by cups-browsed when the printer is plugged in. HPLIP can be left on the system.

What is your device model?

HP Envy 5540

---

