---
title: "1152x864 on a Dell Optiplex GX270 - how?"
date: 2005-05-26
forum: Hardware &amp; Laptops
---

### Post by Xianath on 2005-05-26
Hi all,

I've been trying to get 1152x864 (or any other non-VESA mode) on a Dell Optiplex GX270 for almost 9 months now, to no avail. I don't consider myself a newbie but this integrated Intel video has really drained me of ideas. 

855resolution does not work, it claims to have replaced the mode but does not. I tried running it before even agpgart is loaded (gave it a S11 or S19 in rcS.d) but it's still a no-no. I've gone through every single version of XFree86 and X.Org in the past 9 months, including xserver-xorg 6.8.2-20 which I upgraded to today despite the warnings in the Breezy forums. Still nothing. I've downgraded the BIOS from A03 to A01, upgraded to A04, now A06. Nothing. I've given it custom modelines. Nada. Tried the vesa vs. i810 driver - no good. I believe I've tried everything I could but it still fails.

I'm pretty much clueless at this point. Right now the options for me are either 1024x768 or $400 for a 1280x1024 LCD, and that *really* makes no sense considering this is my work PC.

I've seen others on this forum solve this problem for the GX260 and GX280. Has anyone had any success with getting a non-VESA mode on a GX270?

Kind regards,
Peter

---

### Post by Xianath on 2005-06-09
Never mind. Got a 1280x1024 TFT now.  :grin:

---

### Post by ddhytz on 2005-06-14
[QUOTE=Xianath]Hi all,

this integrated Intel video has really drained me of ideas. 

I'm pretty much clueless at this point. Right now the options for me are either 1024x768 or $400 for a 1280x1024 LCD

[/QUOTE]

You could get a graphics card at very low cost.

---

### Post by NickB on 2005-06-14
Make sure you have updated your bios to at least A06.  Also you need to specify VertRefresh and HorizSync in your xorg.conf file, if necessary (was needed for my dell lcd panel).

Nick

---

