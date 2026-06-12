---
title: "ipw2200 woes"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by GnuKemist on 2005-04-15
I finally got my X40 last night and immediately installed Hoary.  Everything went smoothly with exception to the iwp2200 wireless.  It was detected and I can even pass arguments to it via iwconfig but I just cannot get an IP assigned to it.  I have tried this on a few APs now, either with WEP enabled or off with the same result.

I spent quite some time both at #ubuntu and #ipw2100 (they also support ipw2200) but couldn't come up with an explanation...

Any feedback will be greatly appreciated.

Cheers,

Gnu

---

### Post by gil-galad on 2005-04-15
My roomate has that wireless card and hoary works perfectly on his laptop.  I don't know what to say..... I assume you have tried to assign an ip for it with dhcp?

---

### Post by Gandalf on 2005-04-15
just a little advise, do like me and try to adjust it for the first time using the graphical utility (System -> Admin.. -> Networking), i had the same problem but after i did this i could change then interfaces file and do whatever i want

---

### Post by GnuKemist on 2005-04-15
Well, it's the darnest thing...  Just got back from work, plugged the laptop in and the wifi just works!!!  Just like that!!!  The one thing I did before this, was to download the firmware from [ipw2200.sourceforge.net](http://ipw2200.sourceforge.net) into /usr/lib/hotplug/firmware...  Sooo...  I don't really know what the problem was or how it got solved but...  I'll take it!!! :)

Just to answer some of the questions:  I tried setting the darn thing both through GUI and command line to no avail...  And I tried using DHCP (which my router is setup to do) and static IP...  Like I said before...  It's the darnest thing!

Cheers,

Gnu

---

