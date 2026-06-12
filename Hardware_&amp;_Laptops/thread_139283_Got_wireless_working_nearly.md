---
title: "Got wireless working nearly"
date: 2006-03-03
forum: Hardware &amp; Laptops
---

### Post by Melicous on 2006-03-03
Ok I got my Belkin f5d8010 working with ndiswrapper v9 (not 10 or newer)
I can acces my AP and router wireless

but the problem is that I can't get internet :-k 

Is this some problem in linux (wierd firewall or such) or just those flaky drivers

P.S.
I'm working over vnc cause I only got 1 screen

---

### Post by Jason_25 on 2006-03-03
Is DNS setup?  The name of the DNS server should be in /etc/resolv.conf.

---

### Post by Melicous on 2006-03-03
yep already tried that

copied all settings from my xp pc

Edit:

It was my dns settings (dns hostname table) that were the problem only they were set on my router ??
In winxp these settings were set automaticly (I guess)

and for reference its an
Thomson SpeedTouch 516

---

### Post by Stryker777 on 2006-05-06
I have been working on that for some time and no success.  It doesnt identify at all in the devices.  Just Unknown.  

Any advice?
Thanks

---

### Post by Stryker777 on 2006-05-07
I got the driver in but cant dhcp.  I think it may be time to just buy another lol.
THanks

---

### Post by Stryker777 on 2006-05-09
I gave up on the Belkin.  Tried a Linksys WPC54G with no luck. Turns out it was a v2.  Oh well.  Returning it today and getting a D-Link DWL-G650.
Anyone have good luck with it?  Its listed well in the list so i might as well go for easy this time lol.

---

### Post by Stryker777 on 2006-05-09
Got a netgear wg511t since they didnt have the dlink.  Worked the second I plugged it in.  Im using Dapper with network-manager-gnome and everything including wpa is perfect.
Good luck.

---

