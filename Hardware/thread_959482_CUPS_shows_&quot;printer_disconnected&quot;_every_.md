---
title: "CUPS shows &quot;printer disconnected&quot; every time HP printer is power cycled"
date: 2008-10-26
forum: Hardware
---

### Post by Calmor on 2008-10-26
I see a lot of the "Printer Disconnected" posts online, but I haven't found one similar to the issue I'm having.

I switched an HP printer from a Windows server to a (Myth)buntu server running CUPS.  The printer installed fine and has no problems printing... until I turn the printer off.

Since the printer is at home and is used only a couple times per week, I don't see the need to have it powered on all the time.  Unfortunately, every time I turn it off, I have to delete the printer in CUPS and reinstall it.  Restarting CUPS has no effect.

The printer is an HP PSC-1610.  By powering it off, I mean that I only turn it off on the main panel (standby mode, I guess) - not a full power removal.

Are there any workarounds to this?

---

### Post by sercik on 2009-01-08
I have the same problem with hp1280 connected via usb 
i think that is the problem is because if you restart printer change the device so i have done the following:

lpadmin -p printername -v deviceURI 
if you have only one usb printer you can change devide URI with:
usb:/dev/usb/lp0 or maybe usb:/dev/usblp0 depending of ypur linux OS.

Let me know if it works

[email]aspcicc@yahoo.it[/email]

---

