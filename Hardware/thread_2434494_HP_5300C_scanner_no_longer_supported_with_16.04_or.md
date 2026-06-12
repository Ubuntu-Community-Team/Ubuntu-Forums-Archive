---
title: "HP 5300C scanner no longer supported with 16.04 or 18.04"
date: 2020-01-06
forum: Hardware
---

### Post by Geokimbo on 2020-01-06
The HP 5300c flat bed scanner I had hooked up to an Ubuntu 14.04 machine no longer works after I upgraded to 18.04 via a fresh install.

My symptoms are the same as;
[https://ubuntuforums.org/showthread.php?t=2365463](https://ubuntuforums.org/showthread.php?t=2365463)
and
[https://alioth-lists.debian.net/pipermail/sane-devel/2016-June/034593.html](https://alioth-lists.debian.net/pipermail/sane-devel/2016-June/034593.html)

TLDR - simple scan, xsane and scanimage all report an HP5300C as being connected via a USB. When I try to scan something the scanner light comes on and the shuttle starts to move (1mm at most) before stopping. the scanning app then comes back and tells me it can't communicate with the scanner - *"error during *device I/O" The scanning app can then no longer see the scanner until I power cycle the scanner.

The various pages I have looked at suggest;
[LIST=1]
[*] a permissions problem - scanimage "works" as a user so I don't think so 
[*]a conflict with libsane-hpaio - removing that did not help 
[*]setting the scan resolution to an integer multiple of 100 - 300 was the lowest, 100x  option, simple scan gave me and that did not work 
[/LIST]

scanimage says it is using the avision driver and the avision sane page says it fully supports the HP 5300C albeit an old page.

I had a 16.04 machine available and it showed the same symptoms. My only windows machine ran Win7 which does not have a driver for the 5300C. I could hook it up to an XP or Ubuntu 14 VM to confirm that there is nothing wrong with the scanner but given that it worked fine on U14 last week and that others have had the same issue I doubt that would advance my cause much and is certainly not the long term solution I wanted.

I did open up the scanner and manually moved the shuttle its full length to check that it wasn't stuck. Leaving it fully extended and turning the power on causes the shuttle to return to its stops so I don't think I have a mechanical problem.

I hate turfing perfectly good hardware just because the current OS can no longer talk to it and I don't really want to have old, less secure OSs on the network which was why I upgraded the U14 box in the first place.

Any ideas?

---

### Post by rbmorse on 2020-01-06
[https://www.hamrick.com/vuescan/hp_scanjet_5300c.html](https://www.hamrick.com/vuescan/hp_scanjet_5300c.html)

VueScan is payware, but you can try it for free.

---

