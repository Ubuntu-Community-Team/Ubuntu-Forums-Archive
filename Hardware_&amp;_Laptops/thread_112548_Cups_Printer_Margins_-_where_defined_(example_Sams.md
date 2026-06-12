---
title: "Cups Printer Margins - where defined (example Samsung ML-1410)"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by isoaglib on 2006-01-04
Hi,
I was used to set the default printer margins in the file
/etc/cups/ppd/<printer>.ppd
in the chapter with "ImageableArea".

But when I installed a Samsung printer at Kubuntu Breezy, the default printer margins are:
+ 24 pixel top/bottom
+ 36 pixel left/right

Those margins are independend from the setting in the ImageableArea section in the printer PPD file. Several research directed me to the section with HWMargins. But I was not able to find a connection between those settings and the default margin.

So I have the impression, that those margins are hard coded somewhere. As I didn't see this behaviour with pure/Knoppix Debian, this seems to be something specific for (k)ubuntu.

The funny thing:
I tried to use the lpoption strategy - i.e. call this CUPS tool to set the default margins which are then stored in /etc/cups/lpoptions. But the hardcoded margins overrulled those margins.

My last resort was:
Set my individual printer margins in the kprinter dialog and select STORE there. When I do that as _root_ the margins are used, as long as I select "use user specific margins" in the kprinter dialog.
--> I was no able to set the _default_ margins

I found several information directing to [www.linuxprinting.org](www.linuxprinting.org) where I could do some strange printout scenarios...
Is this really the only way to get smaller default margins the the left and right side?

Thanks for any hints.

---

### Post by manis on 2006-01-07
Hi,
I just bought printer ML1610 (samsung) and install the driver. After finished , I find out that samsung give me a lot of printer model to be selected as a driver. The default driver  for ML1610 is ML1650. When i did test page , the printer did not print at all. What i do is I choose ML1510 as my default driver and everything is fine. I can print text and ilustration.
My point or my suggestion for you  is try to change your default printer and see the result.
Hopefully you can solve the marginal problem.
thank.

---

