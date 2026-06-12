---
title: "Averatec C3500"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by normrobichaud on 2005-06-28
Well, I'm a relative newbie, it helps to live with one of the executives from LPI although I have to pay for my support by doing dishes and vacuuming.   ;-) 

I have the Averatec C3500 Laptop/Tablet and the installation of Ubuntu 5.04 went smoothly for the most part.

In order to get the WAN working, we had to get out the thinking caps and reading glasses.  Via NDISWRAPPER we installed the RaLink RT2500 driver and then the fight was on.

Ubuntu saw the installed driver and the hardware, but didn't marry them up.  Still no network.  We hacked it, downloaded updates including the kernel and just kept plugging away at it, restarting and restarting.

There are a few how-to's out there for setting up the WAN on the Averatec, but the one that worked was at:  [https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo) .

Being a newbie, I can only tell you that without help, I never would have got my WAN working, without which, I cannot work.  I'm glad that Ubuntu was the distro that finally worked, I can find my way around Ubuntu much easier than the other distros.

Grumpy distros that SHOULD have worked on the Averatec:

Mandrake distros over version 8 is afraid of the C3500, kernel panicked each time.
Fedora Core 3 wouldn't lay it's hat on my system and call it home.
Fedora Core 1 installed but the WAN was hopeless.

There were many distros tried, but only Ubuntu works completely with my system.  The only problem I have had in the two days since installing, is that the new Evolution email client hangs my machine when in use.  Uninstalled the Evolution and Firefox packages and replaced with the real Mozilla and Thunderbird.  Works great so far.

Another note, the new Evolution hangs on our IBM Thinkpad where the old one never did, so problems are not limited to the C3500 in that respect I think.

So if you have a C3500, use the latest Ubuntu and get experienced help.  Newbies shouldn't be updated kernels.  Or captains and majors for that matter.  Sorry, couldn't resist.

God bless.

---

