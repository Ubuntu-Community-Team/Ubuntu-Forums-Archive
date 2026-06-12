---
title: "USB Mouse! Help appreciated."
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by Amped-Gaming on 2006-04-21
Hi!

I succesfully Ubuntu today with no problems, apart from when I boot.

When I boot i get the message "USB Takeover Failed! (BIOS BUG)" (Or something along those lines). And my USB mouse goes off, deeming the OS useless.

Anyone got any help? :(

---

### Post by rdominiak on 2006-04-21
Maybu you should change something in your BIOS settings (something connected with USB and maybe mouse - try to find such settings). another possibility is wrong configured X-server (/etc/xorg.conf) but I thing that computer with bad X configured should work until you start X server, so I think that is rather BIOS problem. Look at your BIOS settings, find something intresting and use google.com or write here what you've find.

Unfortunately I have a mouse problem too :/ It turns of after few minutes of using, and then I have unplug it and plug again or restart the Xserver. Maybe it's the Xserver problem (but I have tried many configurations of mouse i xorg.conf) or kernel problem (some time ago i've worked od Windows and everything was ok; I have this problem only on Linux (Ubuntu and Aurox (polish distribution based on RedHat/Fedora); I have not tested other ones). On the other hand, that was cheapest optic USB mouse in the shop ;)

Somewhere in internet I have found that mouse may lost some kind of synchronization (?) and windows is checking that synchronization continuusly for all the time and linux only when device is connected to the computer or somethng like that...

_______

now I have dapper drake and everything is ok :) I'm not sure what was wrong but I think that was something wrong with a kernel.

---

### Post by Slade Winstone on 2007-02-12
Hi, I'm running Edgy, 2.6.17-11-generic, and found a strange, kinda, partial work-around, for this problem:
[http://ubuntuforums.org/showthread.php?p=2143128]("http://ubuntuforums.org/showthread.php?p=2143128")

---

