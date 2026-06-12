---
title: "Printing absolutely DESTROYED! Can I Uninstall/Reinstall CUPS or something???"
date: 2009-01-15
forum: Hardware
---

### Post by OzzyFrank on 2009-01-15
Here is a summary of what has been going wrong with my Canon MP800 using both the generic printer drivers, and the TurboPrint ones (which I installed so I could get better disc printing than the 300dpi the generic one offered). This all started happening either with the Hardy upgrade or an update afterwards. Note there is some info at the bottom concerning limited success after CUPS updates I installed today.
------------------------------------------------------

A few months back, gLabels started messing up the printing on discs, and I first thought it was a problem with that program after an update. Actually, it may have been that too, since I could save them as PDFs and they would print fine through Document Viewer.

However, now I suspect the problem is to do with the whole printing system itself, as I can't successfully print anything anywhere (well, SOME things I now can... more at the bottom)!

gLabels will go to line up the disc for printing (which it seems to do fine) but then just spits it out without actually printing a thing, and now the PDFs which successfully printed in Evince a few weeks back are printing all mangled (like a bit of the label on only the right side of the disc).

I cannot even print a web page from Opera, as it just sits there telling me it is getting ready to print, but never does. This is using either the default CUPS driver or the TurboPrint one.

I know Canon aren't the best when it comes to Linux support, but I have been using the TurboPrint driver (for my MP800) with no problems for a couple of years... till now. I did get rid of the TurboPrint driver and reinstall it again, to no avail. Unless someone has the answer for what is happening here, I have to ask instead:

[COLOR="Indigo"]Can I somehow uninstall the whole printing system, then reinstall it again to see if it fixes things?[/COLOR]

I can assure you the printer itself is fine, as it prints fine in Windows, and in Windows running in Virtualbox while in Ubuntu (which is what I have to resort to in order to print anything while in Ubuntu). I'd like to try and "start from scratch", as the printer has now been rendered completely useless under Ubuntu (which, you would admit, is a pretty sad state of affairs... and something I dare not admit to friends I am trying to convert to Ubuntu!).

After today's CUPS drivers update:

* I just tried printing a basic OOo Writer document, and the program crashed, which is a first! Before, it would just fail to print.

* Then I tried printing a single-page plain text file in Gedit, and nothing happened whatsoever. After a few minutes it did tell me the printer wasn't connected or turned on, so I tried again with one paper setting I termed "Failsafe" as it would always work, and at first that didn't even seem to work... then it printed but only after a message popped up from the top panel saying something like "2.0-root-hub" wasn't there/installed so it used/installed a generic one (sorry - it went by far too quickly to note exactly what it said, and now can't reproduce that as it prints the plain text using that setting without error). However, I can't see how this would have helped, as to me it seems to refer to the USB storage part of the printer... and when I got to check the settings for it, the lack of options like page size etc seems to confirm this. In settings it is listed as **usb://Linux%20Foundation/2.0%20root%20hub?serial=0000:00:1a.7** and "Generic text-only printer". In Printer Properties it does have a media size available, but only Letter.

* Printing a web page in Opera using the "Failsafe" setting now works.

* Disc printing using any of the TurboPrint settings still a no-go. A PDF I have with just a black circle around the centre prints above it and through the actual hole. The generic driver for the disc tray says it is unplugged or turned off.

* My failsafe paper setting, which can now print, uses **usb://Canon/MP800** - but then so do some of my disc printing ones, to no avail (others use the TurboPrint one, which is **hal:///org/freedesktop/Hal/devices/usb_device_4a9_170d_228F43_if1_printer_noserial**).

* Tried creating a new printer with drivers from the database (there was no MP800 so used MP830) and disc printing does as in gLabels, ie lines up the disc carefully before spitting it out unprinted.

Sorry if this info is a bit all over the place, but I hope someone can help, as this is driving me nuts. I would be more than happy to supply additional info from log files or printer settings or whatever, so please let me know where to find the info, and I will post it. Thanks.

---

