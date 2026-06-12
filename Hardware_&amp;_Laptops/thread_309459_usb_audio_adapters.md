---
title: "usb audio adapters"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by shoagun on 2006-11-29
Hi,

My headphone jack broke on my laptop.  I was thinking of getting a usb audio adapter.  Something like this:

[http://www.maplin.co.uk/Module.aspx?ModuleNo=44636&doy=29m11&C=SEO&U=strat15](http://www.maplin.co.uk/Module.aspx?ModuleNo=44636&doy=29m11&C=SEO&U=strat15)

Before I buy anything, I was wondering if anyone knows if this will work on Ubunutu?  They tend to all say "Windows compatible".  Does anyone have one that they know works?

If it helps, I'm running Dapper on a Dell Latitude D810.

Thanks

---

### Post by teitunge on 2006-11-30
Hi.

I do not know this for sure, but I would guess it works the same way as a usb-headset. I bought a cheap one, and when I plug it in and restart gnome it pops up in the "sound-device-list" as a C-Media Headphone set.

I would guess your usb device would do the same, so you could pick it from a list.
Everything says it´s Windows compatible, but ubuntu actually supports most things out-of-the-box, if not, you could probably configure it. 

I say yes, and good luck :)

---

### Post by unlokia on 2006-11-30
How old is your Dell??. I hear that they have excellent support, and if it *is* out of warranty, I would recommend that you get the headphone jack replaced. There is nothing more irritating than USB devices hanging out of each and every port on a laptop!. I looked at the MAPLIN page you refer to: "YOGA" is the brand... can only imagine this thing tying you in knots!:p 

Please visit Dell Support page ---> [http://support.dell.com/]("http://support.dell.com/")

I am sorry if I have not been much help here! :)

take care

---

### Post by shoagun on 2006-11-30
Thanks for the info.  teitunge, i bet you're right.  I'm going to go ahead and try getting one of these things (since they're really cheap on ebay).

unlokia, yes, ideally i would have the jack replaced.  the laptop is pretty new, but i got it second hand, so i don't think i would be able to use any warranty.

---

### Post by shoagun on 2006-12-02
UPDATE:

So, I got a cheap plug and play usb audio converter.  ubuntu automaticallyd detected and I was able to make it my default soundcard.  I had to restart gnome, but after that the thing started to work great.  The only problem is there is no way to control the volume except in the application I'm using.  None of the system volume controls affects it.  I kinda expected that though

---

### Post by shoagun on 2006-12-03
Ok, after some more playing around, I've discovered that things aren't working quite right.  Any sound playing from Firefox still plays out of the onboard soundcard.  xmms and mplayer will play from the usb device, but I can't open more than one thing at once.  

The only way to control volume is in the application or by typing alsamixer in the command line.  The sound controls don't affect anything.

---

### Post by shoagun on 2006-12-03
WARNING:

So it looks like this usb device may have somehow messed up my computer.  Before using it, sound worked perfectly.  After I installed Ubuntu, sound automatically worked.  I could listen to mplayer, xmms, youtube, flash sites, all at the same time.  All I did was plug in a usb audio adapter and play sound off of it.  When I unplugged it, sound is all messed up.  More than one application can no longer use the soundcard.  xmms simply won't play any sound at all and says my soundcard is either being used or not configured properly.  I never changed any settings on anything except change the default soundcard.  When I unplugged the usb device, the default went back to the onboard card, but now I have all the problems I just mentioned.  Restarting didn't help at all.

---

