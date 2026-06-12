---
title: "Gutsy + Propriety Drivers (ATi) = Epic Fail"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by UnWeave on 2007-10-23
Not sure which topic to put this in as I don't know where the problem origniates, so if you have to move it, apologies.

Well, I had been having problems with SUSE (10.3 - 10.2 used to work fine, after the issues I had were ironed out) and Compiz Fusion, and a friend suggested I try Ubuntu... I downloaded the 7.10 Live CD, liked it, and installed. So far so good. 

The problem came when, after install, Ubuntu told me to install the restricted drivers. Up to this point the open source graphics drivers I was using had been fine, except when I tried to change the resolution nothing happened - the dialog box "do you want to keep these settings" etc came up, but the res. was that same (this happened both before and after install, although I did find a bug report on this, at least in the Live CD after googling it). I thought this might be a driver issue so went ahead and installed the restricted drivers. On reboot, ubuntu went into low-res vesa mode and told me that my card hadn't been recognized... So er, didn't really know what was going on there, and I couldn't get the compiz fusion effects to work again (graphics-related errors when I tried to select) after choosing the open source drivers again.

I'm using an ATi 9600XT (RV360 chip, btw).. It's just occurred to me that if the drivers it installed were 8.41.. then the error isn't unusual, as I would need 8.40.. for my non-HD card, but at the time I just pointed and clicked...

By this point I was a bit sick of all the problems, ran fixmbr from my WinXP recovery disc and loaded into XP as normal... And now Windows isn't recognizing my monitor (Compaq FS740).. It's set to default monitor and I can't get it above 60Hz. So, I mean, does that sound like a hardware issue or has ubuntu just... well, done something bad?

I'd appreciate any advice you can give me, and in the mean time I'm going to try and get this monitor back to normal...

Thanks.



[EDIT: I managed to get my monitor from "Default Monitor" to "Plug and Play Monitor" in Windows, and now I am back to 75Hz with the right resolution etc, but I'm still none the wiser as to why it happened]

---

### Post by UnWeave on 2007-10-23
No one got any ideas? :(

---

### Post by Jive Turkey on 2007-10-23
I'm having similar issues, it all worked fine until I installed the fglrx driver and connected my second monitor.  The settings in xorg.conf appear to be ignored, aticonfig is of no use and this new "Screens and Graphics" GUI appears to do nothing, it also thinks my 21'' CRT can only do 640x480 or 600x800.  My other monitor isn't detected correctly and when I point it to the correct settings they just default back to whatever they were before, (unusable).

---

### Post by UnWeave on 2007-10-24
That does sound like the exact same thing tbh... I don't suppose you've got any further with this since that post have you? I managed to get the Windows end of the problems sorted (it had uninstalled the monitor. . .) and I am contemplating reinstalling Ubuntu and maybe tryig Envy, if there's is a version of it for Gutsy out yet? I haven't checked thus far.

Oh, also (Jive Turkey), what gfx card do you have?

---

### Post by Jive Turkey on 2007-11-04
I'm using the radeon9800Pro.  I just got fglrx 8.42.3 working a few minutes ago.  I used this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

I hope it works for you too.

---

