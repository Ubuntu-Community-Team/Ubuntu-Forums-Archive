---
title: "LIve 9.10 CD can't get on Internet..."
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by 2912pwil on 2009-10-30
Dear all, and thanks in advance for any suggestions...

Downloaded Koala, both 64 & 32 bit...cut CD's, tried them by booting off CD first (as I have for about 3 years now..) Immediate impression - hey, looks OK guys! (Thanks everyone..!!)

But (both 32 & 64 bit) although plugging in Ethernet cable I get message saying I'm connected I can't get out onto the net.  Ditto with wireless.  (Hub/Router is a D-Link DSL-G624T).  I've run this rig for a year or so with various SW, worked fine all along.  So I'm confused...

The Hub/Router I've used with the same hardware (Laptop is a DELL 1525).  I've been running dual-boot Vista & 9.04 for some 6 months (and similar before...), no problems...  So I know the net works, the router works, the cable works (I'm using them all now back on 9.04).. weird...!!

Any suggestions??

I tried connecting a mobile-broadband (mobile 'phone network) 3G Dongle, Huawei, from "3" here in UK.  It worked!! (which I never managed with 9.04!!) So Firefox and getting on the Internet is OK, but I'm stumped as to why I can't get through the "wired" route (And am thus nervous of doing an upgrade/install).


Cheers!

2912pwil

---

### Post by BarisBlaq on 2009-10-30
Might be this bug
[http://ubuntuforums.org/showthread.php?t=1304900](http://ubuntuforums.org/showthread.php?t=1304900)

---

### Post by 2912pwil on 2009-10-31
Thanks for the hint BarisBlaq...

Nope, 'twasn't that... I re-booted with " choose "acpi=off" from the F6 menu of live cd.  ".. same problem...

But I did a bit more investigating: It's really weird: I can get into the management console of the router/hub.. see all the usual stuff but can't get out on the Net -- I've looked through the various Firefox Network settings & compared them with my working, live, 9:04 system and can't see anything..

Stumped!!! 

Anyone??

Regards & Thanks in advance!

---

### Post by kiff on 2009-10-31
I have a similar problem. I recently upgraded one of my systems to 9.10, and can no longer connect to the net. When I attempt to connect via ethernet or wireless, NetworkManager notifies that I am connected, but when I try to go to a page in Firefox (e.g. my gmail account), I get the message in the status bar: "Connecting to mail.google.com...", a long wait, and then the connection times out. 

The interesting thing is that I can ping any site without trouble.

I though maybe it was something to do with the proxy settings, but I have checked that and that doesn't seem to be it.

Any suggestions would be greatly appreciated!

---

### Post by kiff on 2009-10-31
2912pwil, have you tried disabling IPV6? I did it in Firefox, now Firefox works for me. Now I just need to disable IPV6 across the board and the issue should be fixed.

---

### Post by 2912pwil on 2009-10-31
Kiff:

re> 

have you tried disabling IPV6? I did it in Firefox,

Perfect!!! 

Now running off live 9.10 CD, thanks everyone...

(And I didn't realise what a problem IPv6 was - interesting posts out there!!).

However I'm still confused as to why I could get out on a mobile broadband dongle without the change...

Thanks again

---

### Post by 2912pwil on 2009-11-29
Further to my earlier...

Been playing around with a new router (3g, Edimax as it happens) and having got that up 'n running thought I'd try the LiveCd again (64bit 9.10).. 

Booted:
Start Firefox...
Out onto the Internet, no problem...

So,,,, it looks like the "problem" is some issue/incompatibility between 9.10 and some routers (certainly in my case the D-Link DSL-G624T).

Hope that helps someone else...

---

