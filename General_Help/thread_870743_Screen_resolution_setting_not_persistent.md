---
title: "Screen resolution setting not persistent"
date: 2008-07-26
forum: General Help
---

### Post by b9k9kiwi on 2008-07-26
I am new to Linux but I have been around long enough to know that when you get two distinct problems you shouldn't;

1 assume that they are related.
2 assume that they are not :)

I built a new system especially to run Ubuntu (specs below) and carried out a trouble-free installation with a (used) 14" Siemens MCM153-V CRT monitor.  

After a week or so, just as a short-term experiment, I switched the monitor to a (new) Chimei CMV938-D widescreen LCD screen (from my other system).  During this period Firefox 3 was installed in place of version 2.  No problems before I switched to a recently acquired (used) 15" TPG 770H CRT monitor.  At this point I had a problem with Firefox in that it loaded full-screen hiding both menu panels.  This forum pointed me to fixing this by reinstalling Firefox 3 - which, indeed, fixed the problem.

Having done that my preferred screen resolution of 1024x768 now tends not to 'stick' from one session to another.  When I boot, the screen resolution tends to load at 640x400 and preferences/screen resolution does not give me the option to change it.  Restarting does not result in the preferred 1024x768 being loaded but a shut down and fresh boot does.

This issue does not appear to be intermittent (but has not been apparent for a long enough period to confirm that).  At this point the problem is nothing more than a nuisance but I would love to fix it.

Any hints?


ASUS M2N-MX SE Plus All in One Motherboard (new)
AMD Athlon 64 X2 Dual-Core 4800 (new)
1GB DDR2 667 Ram (new)
160Gb Seagate ATA ST3160815AS Sata HDD (used)
msi nvidia nx6600 256MB PCIe (used)

---

### Post by bsmith1051 on 2008-08-28
you never mentioned which version of Ubuntu you are running, nor which video driver.  Since you have a mid-range Nvidia did you install the Ubuntu-supported 'Proprietary' driver, or even the official Nvidia driver?

In general, it sounds like your xorg.conf has gotten cluttered with multiple monitor settings and is 'selecting' the wrong one now.

P.S.  I really doubt it has anything to do with Firefox.  Instead, I think swapping monitors is the cause (though that SHOULD NOT cause a problem, oh well...)

---

### Post by jonian_g on 2008-08-28
Take a look here:

[http://ubuntuforums.org/showpost.php?p=5538065&postcount=3](http://ubuntuforums.org/showpost.php?p=5538065&postcount=3)

---

### Post by bsmith1051 on 2008-08-28
looks like there's a utility (see previous suggestion) that makes it easy, i.e., no mucking around in the .conf file directly.

---

