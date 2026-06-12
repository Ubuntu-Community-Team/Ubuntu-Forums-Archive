---
title: "Recommend a usb dongle for recording OTA HD..."
date: 2015-07-14
forum: Hardware
---

### Post by twgray on 2015-07-14
I'm not sure that this is the right forum for this question but I'll start here.

Can someone recommend the best (for use with Ubuntu) usb dongle for recording Over The Air HD television?  I am moving into an area that has great over the air digital TV signal reception (welcome to the 20th century) but limited internet and cable tv access, so I am researching the best solution for recording OTA digital HD.  I prefer an external solution that can be used with a laptop rather than one of the ubiquitous TV cards.

Thanks for any enlightenment you may have.

---

### Post by Vladlenin5000 on 2015-07-14
Most dongles, as well as their PCI or PCI-e counterparts are already supported at the basic level. Meaning: Some will be recognized straight away, many will need a proprietary firmware which is available in Ubuntu repositories and suggested at the Additional Drivers tool but otherwise fine and a few that don't work or require too much work for what it is... The bundled remotes often require the bundled (Windows) software. In a nutshell, most current tuner chipsets will work fine in Ubuntu albeit partially.

In order to suggest some hardware we need to know which digital TV technology first. Not all chipsets have support for more than one.
If we were talking about Europe and/or DVB-T/T2 this [humble and unbranded HD DVB-T/T2 USB TV Stick with MPEG4 support]("https://www.chinavasion.com/china/wholesale/Home_Audio_Video/Home_Theater_AV/DVB-T2_USB_TV_Stick/") would be enough.

---

### Post by twgray on 2015-07-15
I am talking about the US OTA digital stream.  Which work best for that application?

---

### Post by Vladlenin5000 on 2015-07-15
You need ATSC then...
Sorry, no suggestions. The [EZCAP]("http://www.dx.com/p/ezcap-usb-2-0-hybrid-atsc-digital-qam-hdtv-tv-tuner-receiver-with-remote-controller-42265") probably works but it's sold out. You can search in the usual stores - AliExpress, eBay, Amazon, etc. -  then google about the brands-models/chipset + ubuntu of those available to you.

---

### Post by Bucky Ball on 2015-07-15
I use an Ezycap DVB-T tuner. Works 'out of the box' with Ubuntu 14.04 LTS. 

Anything with the Realtek RTL2832U chip will work fine (that is what is in the Ezycap). The chip inside is more important than the brand and model. Good luck with TV on Ubuntu. :)

---

### Post by coffeecat on 2015-07-18
*Thread moved to **Hardware**.*

---

