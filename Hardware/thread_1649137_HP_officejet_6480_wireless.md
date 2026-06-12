---
title: "HP officejet 6480 wireless"
date: 2010-12-19
forum: Hardware
---

### Post by aeronutt on 2010-12-19
So, up until a few weeks ago, my wireless connection to my HP J6480 had been mostly flawless. Now, I can't seem to get it connected. Here's what I've done so far in trying to debug the problem.

- When I use the printer menu (the menu and commands physically on the printer) and ask it to test the wireless connection to the router, it reports back 'connected', and 'pass'.
- When I look at my router, it thinks it's connected to the printer.
- When I run hp-setup, and try to search for the printer, I get an "error: Unable to send broadcast DNS packet: [Errno 1] Operation not permitted"
- When I try to ping the printer, I get "Destination Host Unreachable"

Any ideas?

---

### Post by aeronutt on 2010-12-20
FYI, just as a sanity check, I reloaded a wireless router state from a date that I know the printer was working. And that didn't help.

Any ideas on what next steps and/or commands to debug this problem?

---

### Post by aeronutt on 2010-12-21
Help anyone?  Seems HP is one of the better supported printers for Linux, and Ubuntu is one of the better supported Linux distro's, yet getting this HP printer to work with Ubuntu is turning out to be a deal killer.

---

### Post by coffee412 on 2010-12-21
> **aeronutt said:**
> Help anyone?  Seems HP is one of the better supported printers for Linux, and Ubuntu is one of the better supported Linux distro's, yet getting this HP printer to work with Ubuntu is turning out to be a deal killer.

In your hp menus on the printer could you print out the network info and provide the ip address assigned to the printer and the other stuff?

Also, The network info from the computer your trying to print from.

Then we can get started.

coffee

---

### Post by aeronutt on 2010-12-21
Well, that's the only clue I needed..should have thought of this before. Not sure WHY, but here's my fix: I set the printer IP address manually (versus automatic), re-run hp-setup, entering the IP address into that tool, and now, all is well.

Thanks!!!

---

