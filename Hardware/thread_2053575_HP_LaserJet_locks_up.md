---
title: "HP LaserJet locks up"
date: 2012-09-05
forum: Hardware
---

### Post by derekn on 2012-09-05
I'm trying to get an Ubuntu 10.04 system to print to an HP LaserJet 3052 attached via the network.  I had it working fine for a while, but something must have been changed or updated -- I have no idea what changed, and it's driving me nuts.

I've tried uninstalling all hplip* packages and setting it up with the standard "add printer" thing, manually entering the IP address for the printer (which ends up with a "socket:" URL).

I've also tried installing hplip and running hp-setup, and letting it auto-detect the printer (which ends up with an "hp:" URL).

In both cases, it appears to find the printer without any errors.  It auto-detects the model number, so I think it must be communicating with the printer.  When I try printing, the document shows up in the queue, but never prints (same results if I print a test page or print from Open Office).  The activity light on the printer never blinks.

The weird thing is that attempting to print seems to lock up the printer.  I have another system (running Slackware) which can print just fine.  But as soon as I try to print anything from the Ubuntu box, the printer will no longer print from the Slackware box either.  Power-cycling the printer fixes that problem (but of course the Ubuntu box still can't print).

Network connectivity is ok -- I can access the printer's built-in web config page from both Linux machines.  And printing a test page from the web config page works.

Has anyone seen something like this?

---

