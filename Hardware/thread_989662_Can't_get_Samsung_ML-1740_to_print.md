---
title: "Can't get Samsung ML-1740 to print"
date: 2008-11-21
forum: Hardware
---

### Post by richmr2174 on 2008-11-21
Hey all,

I've got an ML-1740 that once printed via my kubuntu (8.04) install and now won't.

The printer is recognized by the model name in the print manager.  Checking its properties shows it is getting all the relevant data from the system.  lsusb shows the printer:

Bus 001 Device 002: ID 04e8:324c Samsung Electronics Co., Ltd ML-1740 Printer

The local print server is working in the sense that it accepts and queues jobs, but it never moves past "processing."  

The printer will print its internal test page and it will print from WindowsXP, using the same machine (dual boot--well triple boot really, but that's not important right now).  

I don't see anything bad in the cups error log, just some standard logging messages.

I've tried the "off-on", the "pull and replug", and the reboot methods of troubleshooting.

Its got me kinda flumoxed.  It worked the very first time I tried it after my Kubuntu install, but hasn't since.

Possible changes:  I was trying to get it to network print with my wireless XP machine, but don't remember making any changes to settings since I was in a hurry and just rebooted into XP.

I've updated all my packages.

Any ideas?

I appreciate it,

Mike

---

### Post by SeePU on 2008-11-21
I'd like to try and help but my suggestions might not be of any help.

Have you tried pointing your browser to the CUPS page?:
[http://localhost:631/](http://localhost:631/)

Also, since the printer doesn't seem to do anything when you try to print, you might try seeing what is going on in the print jobs manager?  It sounds like some network configuration change might have had the printer hang somehow.   I would check the website above, any network settings regarding the printer and any print jobs manager/settings.  That would be my first step towards finding a solution.  I think the troubleshooting involves covering the most obvious and then moving from there.

---

### Post by Striker_XF35 on 2008-11-22
I don't have this printer but I will try to help anyway.
Try reinstalling the drivers in ubuntu, if that doesn't work I'm not sure what will.
Also, you mentioned triple-boot, one thing you could check (though what use it would be I dont know for sure) is if it will work with your third OS.
And finally, just to clarify, it sounds like you were playing with the network setting in ubuntu, NOT windows correct?

---

### Post by richmr2174 on 2008-11-26
I pointed to [http://localhost:631/](http://localhost:631/) as asked and the printer server pages are there and happy to see me.  So I think the printer server is working fine.  I'll have to check the printer drivers still.

Thanks

Mike

---

