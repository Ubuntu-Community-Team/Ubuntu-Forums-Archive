---
title: "[SOLVED] Is a DRIVER considered SOFTWARE?????"
date: 2008-11-17
forum: Hardware
---

### Post by Kellemora on 2008-11-17
Hi Gang

Sorry, didn't know exactly WHAT to put as the Subject, but that pretty much says it all.

I use a Konica/Minolta color laser printer.  The driver for it is pretty great, once you find all the hidden things in it and where they are located, but I hit a snag.  It requires software to change the toner cartridges on the model I have.

So I tried something.  Since I can print from programs running in Wine I thought, let me try something here.  I loaded the Windows software that came with the printer in WINE, not the driver, just the control software that shows status reports and settings and a method to change the toner cartridges.  It WORKED!  And the features of that program were now available.

So that got me to thinking, ut oh, I know that CAN be dangerous, hi hi.  I downloaded the Windows software for my VERY POPULAR scanner, which is NOT Supported in Linux for some reason, again not the driver, just the software.  All of the programs seem to work just fine from stored files.  Naturally if I hit SCAN it says no scanner found.

Well, a driver IS software, and WINE can obviously see the USB ports.  I think drivers must be installed with the Kernel somehow though.

But my question here is, if a driver is just device controlling software, WHY can't it be loaded through WINE and run from there for a device connected to a USB port?????

I wouldn't have asked this if my printer software didn't allow me to send or retrieve info to and from my printer!  But since it DOES, why not something else?????

I know I'm MISSING something MAJOR here, like my printer DOES have a Linux driver that opens the port? to the printer so the software can access it probably through that driver somehow.

Just Curious is all, as I see no way to INSTALL a driver for a device through Wine........

Nonetheless, it is an interesting question to ponder!

TTUL
Gary

---

### Post by markjensen on 2008-11-17
I am thinking that the difference is that the printer was recognized natively in Linux, and therefore your Windows/wine software that accessed it was able to work.

With your scanner, if sane cannot recognize it and work with it, then I don't think that the Windows software drivers will work.

Unless someone is able to start up some project similar to "ndiswrapper" but for scanners instead of wireless cards.

---

### Post by bapoumba on 2008-11-17
Moved to Hardware.

---

### Post by cariboo on 2008-11-17
The reason your printer software works in Wine is that the printer is well supported. You just haven't found the program you need to change toner cartridge. If a device is supported, whether you run the software natively, or using wine it will work. If it isn't supported then it isn't going to work.

Jim

---

### Post by Kellemora on 2008-11-17
Thanks guys

That's pretty much what I figured!

But it was still interesting that I had access to all the features of the printer once again!  In Wine that is!  But the Linux print driver is actually MORE POWERFUL as far as things you can do with it.  I'm most impressed with it!

I knew it couldn't be that simple or we would have no reason for all the problems with coming up with drivers.
But one never knows until they ask!

I'm going to mark this solved!

Thanks

TTUL
Gary

---

