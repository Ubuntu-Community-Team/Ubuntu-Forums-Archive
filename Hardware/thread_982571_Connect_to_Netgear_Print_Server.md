---
title: "Connect to Netgear Print Server"
date: 2008-11-14
forum: Hardware
---

### Post by bogey on 2008-11-14
I am using Hardy Heron, dual booting with XP.  I have a Netgear wireless print server hooked up to my computer (actually it is hard wired to my desktop), Epson printer hooked up to the print server.  Printing works fine in Windows.

How can I connect Ubuntu to my print server?  

I was reading one file about hooking up to a Belkin server and it said to select New Printer - AppSocket/HP JetDirect and then enter host address.  I don't know what the host address of the print server is nor how to check.  Not sure if this is the right method or not.  Is there a how-to out there on how to set this up?  I can't seem to find it.
Thx

---

### Post by kansley on 2008-11-18
I did it on 8.04 and recently on 8.10 with a Canon PIXMA MP530. I don't remember all the 8.04 details, but they're close to those on 8.10, which are:

- System, Administration, Printing, to get a Printer Configuration window.  
- New printer.
- You'll get a choice of options.  You want to choose an AppSocket device, then type the IP address for the Netgear Server into the host box.  On mine it's 192.168.0.204, but you can find your in the instruction manual.  It's likely the same.
- it'll ask you about what kind of printer.  etc, etc, etc.

I haven't gotten it to scan yet, though.  Good luck.

---

