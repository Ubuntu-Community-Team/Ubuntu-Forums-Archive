---
title: "Radeon HD 4870 on Linux?"
date: 2008-07-23
forum: Hardware
---

### Post by Ajantis on 2008-07-23
I've been using my old Radeon 9550 for few years and my struggle with Linux was a real pain. I'm buying myself new computer right now and I was thinking about GeForce 8800 GTS. However my friends recommend me ATI HD 4870, which seems to be faster.

How does the situation with ATI drivers on Linux look now? Will I be able to easily install drivers (proprietary?) and use Compiz/games?
Or maybe I should rather stick to 8800?

---

### Post by Milyardo on 2008-07-23
ATi drivers for linux are very different from one year ago. This artical will be very helpful to you.
[http://www.phoronix.com/vr.php?view=12558](http://www.phoronix.com/vr.php?view=12558)

---

### Post by Ajantis on 2008-07-23
Seems like the support for ATI carts has significantly increased since my adventure with Radeon 9550.

In other words (I'm pretty new to Linux hardware) - I will be able to fully use it right out of the box?

---

### Post by silvanus2005 on 2008-07-23
[http://www.ubuntuhcl.org/browse/search?offset=0&category=&manufacturer=36&keywords=](http://www.ubuntuhcl.org/browse/search?offset=0&category=&manufacturer=36&keywords=)
Take a look there.

---

### Post by Ajantis on 2008-07-23
Thanx, nice site. Unfortunately it doesn't say anything about 4870 :/

---

### Post by silvanus2005 on 2008-07-23
Try there:
[http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html](http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html)

---

### Post by Xinkill on 2008-07-23
I have the same card and it runs flawless. Even with the hardware drivers from Ubuntu.

But i need to know, anyone here got the same card with dual-screen and succeed in enabling compiz-fusion?
It seems when i enable dualscreen i loose the ability to use compiz-fusion.

---

### Post by Bateluer on 2008-07-25
> **Xinkill said:**
> I have the same card and it runs flawless. Even with the hardware drivers from Ubuntu.

But i need to know, anyone here got the same card with dual-screen and succeed in enabling compiz-fusion?
It seems when i enable dualscreen i loose the ability to use compiz-fusion.

If I may ask, how did you deal with the firmware fan issue, or did you simply get a more recent card with it already resolved in the VGA bios?

---

### Post by Bateluer on 2008-07-27
Nobody's running a 4870 under Ubuntu? Guess I'll be the guinea pig then.

Edit - Up and running with 8.04.1 installed right now. The ATi FGLRX 8.7 drivers installed in a snap without a single problem, however, there doesn't seem to be any way to do the fan profile tweak under Linux that you do in windows. Because of this, the 4870 quickly heats up to 80C. :(

ATI needs to either write a hotfix for this or release a fixed BIOS file that resolves the issue in the card's bios.

---

### Post by Ajantis on 2008-07-29
Perhaps some of you coule help me then. I got the card yesterday and somehow I can't get it to work properly.

I downloaded proprietary drivers from ATI site and install it with X closed. Then aticonfig --initial and after that the systme goes blank before the login screen.

Any idea what may be wrong?

---

### Post by stchman on 2008-07-29
> **Ajantis said:**
> I've been using my old Radeon 9550 for few years and my struggle with Linux was a real pain. I'm buying myself new computer right now and I was thinking about GeForce 8800 GTS. However my friends recommend me ATI HD 4870, which seems to be faster.

How does the situation with ATI drivers on Linux look now? Will I be able to easily install drivers (proprietary?) and use Compiz/games?
Or maybe I should rather stick to 8800?

Nvidia cards work far better with Linux that the ATI/AMD models do.  It has gotten better, but nvidia is the better choice.

I have the 8800GT and it works perfectly after restricted driver install.

---

### Post by Ajantis on 2008-07-29
I tried Catalyst 8.6 instead of 8.7 and everything seems to work just fine. :) Thanks :)

---

### Post by Bateluer on 2008-07-30
I followed the guide to installing ATI drivers on the Ubuntu community docs. Using that, I was able to install the 8.7 drivers without a hitch, aside from the fan problems.

---

### Post by markbuntu on 2008-07-30
I just got an fglrx update for my amd64 Hardy and it was the 8.6 driver, fglrx 8.501.

---

### Post by Ubuntiac on 2008-08-10
I'm absolutely loving mine after switching from an Nvidia 8600GT (with the evilest driver I've ever encountered). An important caveat on installing it though:
[http://ubuntuforums.org/showpost.php?p=5559469&postcount=2](http://ubuntuforums.org/showpost.php?p=5559469&postcount=2)

---

### Post by msn0005 on 2010-09-23
I have ATI Radeon 4870 1GB by Sapphire.

In Window 7, there are no problems with the fan. Its quiet at idle, louder when gaming. Thats normal to me.

But in Ubuntu 10 32bit or 64bit, the fan just won't slow down. Its so noisy that i just lost to mood to use it.

I tried installing all the latest ubuntu version including the beta 32 and 64bit. I try installing the Graphic Card driver from ATI, no change to the fan and even worst there is now a refresh problem, it become really laggy or choppy.

This problem been on Ubuntu 9, thats like 3-4 years ago and still no fix.

---

### Post by Citizen225 on 2010-12-18
I just installed Ubuntu 10.10 x64 with my ATI HD4850.
The fan was going full speed. I installed the proprietary ATI FGLRX drivers and rebooted.
At the command line I ran
aticonfig --initial -f

Then I set the speed:
aticonfig --pplib-cmd "set fanspeed 0 35"

I got silence!

Thanks to **sylvainrb** and this thread:
[http://art.ubuntuforums.org/showthread.php?p=9366671](http://art.ubuntuforums.org/showthread.php?p=9366671)

---

