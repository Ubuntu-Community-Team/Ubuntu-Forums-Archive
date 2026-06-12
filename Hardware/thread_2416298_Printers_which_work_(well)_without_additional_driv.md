---
title: "Printers which work (well) without additional driver installation in 18.04"
date: 2019-04-08
forum: Hardware
---

### Post by mangocats on 2019-04-08
Hi,

We are developing an Ubuntu 18.04 based system that usually doesn't have a printer, but some customers may optionally add a printer to it later on.  We would like for our customers to not have to do anything beyond plug-and-play their printer if they choose from a list of printers which we have pre-qualified for them.

Is there a place I can look for this standard supported printers options list?

Thanks,

---

### Post by Autodave on 2019-04-08
I am not sure that there are any that are plug-n-play.  For simple printing, HP will pretty much just work. But, for scanning, you will have to add a package or two.  Perhaps the packages could be installed even w/o a printer connected, but that is above my pay scale to say for sure.

---

### Post by SeijiSensei on 2019-04-08
HP and Brother printers are well-supported.

I would suggest trying a couple of likely options and making sure the distribution you are distributing to your clients has the appropriate drivers installed before shipping Linux.

Also are these USB printers or network printers?

---

### Post by brian_p on 2019-04-08
> **mangocats said:**
> Hi,

We are developing an Ubuntu 18.04 based system that usually doesn't have a printer, but some customers may optionally add a printer to it later on.  We would like for our customers to not have to do anything beyond plug-and-play their printer if they choose from a list of printers which we have pre-qualified for them.

Is there a place I can look for this standard supported printers options list?

If you can control what is in the shipped cups-browsed.conf and the printer is on the network, you have all you need at

[https://wiki.debian.org/QuickPrintQueuesCUPS](https://wiki.debian.org/QuickPrintQueuesCUPS)

---

### Post by mangocats on 2019-04-09
Thanks for the replies.  Some more detail: we only need printing (and only monochrome at that), scanning functions are actually not desired.

Connection is primarily via USB, but WiFi direct is a strong second option - network a distant third due to the support issues inherent in doing anything on other peoples' networks.

I have qualified a Samsung 2020 (basically a rebranded HP) laser, and it works well with the custom driver installed - but for the future, for instance when the 2020 is no longer in production, it would be nice to have a shopping list for the customers that doesn't require a software update from us to support the new printer.  I understand that Apple has done a lot with Internet Printing Protocol (IPP) and that Linux has benefited from this in recent years.  I think that printers like:

[https://www.usa.canon.com/internet/portal/us/home/support/details/printers/inkjet-single-function/ip-series/ip110?tab=drivers_downloads](https://www.usa.canon.com/internet/portal/us/home/support/details/printers/inkjet-single-function/ip-series/ip110?tab=drivers_downloads)

are connecting through a standard like IPP / Gutenprint (at least according to this:)

[https://forums.linuxmint.com/viewtopic.php?t=262715](https://forums.linuxmint.com/viewtopic.php?t=262715)


Our systems are going to start going out to customers later this year, and the longer they can last in the field without software updates, the better - they're mostly run air-gapped, no internet connectivity.  My desire is to be able to produce a list of compatible printers without a lot of "misses" when we get the first samples in hand to try and see if they will work with our existing software distribution.

Bonus challenge: printer needs to fit on a 15x17" tray - most inkjets these days come with scanners included, and are just a bit too large.

---

### Post by brian_p on 2019-04-09
> Thanks for the replies.  Some more detail: we only need printing (and only monochrome at that), scanning functions are actually not desired.

Connection is primarily via USB, but WiFi direct is a strong second option - network a distant third due to the support issues inherent in doing anything on other peoples' networks.

You would find ippusbxd ideal for your purposes. On Ubuntu it works OTB. For maximum customer satisfaction - ship it with the systemd files operative.

> I have qualified a Samsung 2020 (basically a rebranded HP) laser, and it works well with the custom driver installed - but for the future, for instance when the 2020 is no longer in production, it would be nice to have a shopping list for the customers that doesn't require a software update from us to support the new printer.  I understand that Apple has done a lot with Internet Printing Protocol (IPP) and that Linux has benefited from this in recent years.  I think that printers like:

M2020? An AirPrint device, if I am not mistaken. No drivers needed.

> [https://www.usa.canon.com/internet/portal/us/home/support/details/printers/inkjet-single-function/ip-series/ip110?tab=drivers_downloads](https://www.usa.canon.com/internet/portal/us/home/support/details/printers/inkjet-single-function/ip-series/ip110?tab=drivers_downloads)

are connecting through a standard like IPP / Gutenprint (at least according to this:)

[https://forums.linuxmint.com/viewtopic.php?t=262715](https://forums.linuxmint.com/viewtopic.php?t=262715)

Definitely an AirPrint printer. No driver installation needed with ippusbxd.


> Our systems are going to start going out to customers later this year, and the longer they can last in the field without software updates, the better - they're mostly run air-gapped, no internet connectivity.  My desire is to be able to produce a list of compatible printers without a lot of "misses" when we get the first samples in hand to try and see if they will work with our existing software distribution.

Bonus challenge: printer needs to fit on a 15x17" tray - most inkjets these days come with scanners included, and are just a bit too large.

Get anything with AirPrint that fits other criteria you have.

---

