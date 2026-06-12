---
title: "What happened to the kernel 2.6.26/cypress_m8 fix for Earthmate LT-20 GPS?"
date: 2008-09-11
forum: Hardware
---

### Post by rokky on 2008-09-11
I can see Bill Marr's posting on July 15, 2008 ( [http://ubuntuforums.org/showthread.php?t=220821&highlight=earthmate&page=3](http://ubuntuforums.org/showthread.php?t=220821&highlight=earthmate&page=3) ) on an archived thread about this problem.  It states the "new" 2.6.26 kernel has a fixed cypress_m8 module that handles all versions of the LT-20 GPS receiver.

However, that thread is archived, and thus cannot be updated with this query.   My kernel version for 8.04 is only at 2.6.24-21, and that was just updated within the last few weeks by Update Manager, so something has gone missing here in getting this fix out to those of us who would like to be able to use our LT-20's with Ubuntu instead of Windoze (PClinuxOS 2007 with its older kernel and module worked fine when I tried that).

I had tried a few months ago with 7.10 (Mint) to do the manual recompile of the cypress_m8 module with the workaround fix, but make just could not seem to get all its dependencies sorted out to work for me.  I did a lot of searching/experimenting with configuring make to no avail.  I set it aside, and kept on booting to Win2K for my GPS stuff until I got a Garmin dedicated unit, which is nice ("It just works"), but it is a lot more limited than what I could do on a PC with its bigger screen and richer programs like Roadnav and GPSdrive (and Street Atlas in Windows).

I had hoped this would be sorted out with 8.04's release, but found same old, same old "linux-2.6.24/drivers/usb/serial/cypress_m8.c: cypress_m8 suspending failing port 0 - interval might be too short" in /var/log/messages.  

TIA,
rokky

---

