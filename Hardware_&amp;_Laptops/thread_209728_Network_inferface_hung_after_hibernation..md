---
title: "Network inferface hung after hibernation."
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by sigmason on 2006-07-05
I've read all the posts I can find about this (so it's not an RTFM issue).

Does anyone have their network interface working after a hibernation?

In my Dell Latitude C800 if I hibernate I end up having to disable/enable in network-manager to get the interface back operational.
Is this a problem limited to the odd nature of the 3Com modem/network card in my Dell?

So let's here it, anyone have network interface issues after hibernate or suggestions on fixing the one I'm experiencing...starting to think I need to resort to udev rules.

sigmason

---

### Post by cracker on 2006-07-05
Do you use DHCP? If so, what's the lease time on the addresses? I run into problems with my machines, linux and windows, when my router crashes, because of DHCP lease times, and used to have the same issue when I used hibernation.

---

### Post by sigmason on 2006-07-05
[QUOTE=cracker]Do you use DHCP? If so, what's the lease time on the addresses? I run into problems with my machines, linux and windows, when my router crashes, because of DHCP lease times, and used to have the same issue when I used hibernation.[/QUOTE]

Yes I am using DHCP.
My lease times are 1 day at this location, 12 hours at another and 2 days at the third.

I suppose that is DHCP is the problem in my case, then the question is...should not the network interface preform DHCP again when it reloads the interfaces file after hibernation...afterall it does so when it loads it at normal boot.

Should I create a udev rule to push DHCP with dhclient3 to fix this...or is that bad practice?

sigmason

---

