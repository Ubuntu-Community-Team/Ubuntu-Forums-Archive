---
title: "Hardware issue"
date: 2011-04-13
forum: Hardware
---

### Post by .mouse on 2011-04-13
I dual boot windows and ubuntu.  I only use windows for playing games but lately every time I try to play a game in windows the screen goes black and says no input detected and the computer's fans start running at max speed.  There's no beeps or anything else to determine what's going on.  At first I thought this was just a windows issue but then it happened in ubuntu too which means it certainly must be the hardware but I'm not sure if it's the video card, motherboard or processor.  I took out the video card for a bit to see if it does it again but because the onboard graphics chipset is so underpowered it would be hard to test it on many games so it's really just a waiting game.  Is anyone familiar with these symptoms?

---

### Post by kiddfroster on 2011-04-13
> **.mouse said:**
> I dual boot windows and ubuntu.  I only use windows for playing games but lately every time I try to play a game in windows the screen goes black and says no input detected and the computer's fans start running at max speed.  There's no beeps or anything else to determine what's going on.  At first I thought this was just a windows issue but then it happened in ubuntu too which means it certainly must be the hardware but I'm not sure if it's the video card, motherboard or processor.  I took out the video card for a bit to see if it does it again but because the onboard graphics chipset is so underpowered it would be hard to test it on many games so it's really just a waiting game.  Is anyone familiar with these symptoms?

I would say that your video card may be failing. What brand and model is it?

---

### Post by .mouse on 2011-04-13
> **kiddfroster said:**
> I would say that your video card may be failing. What brand and model is it?

It's a evga geforce 9600 gt.

I'm almost certain it's the graphics card now.  I took the card out and hooked up the monitor to the onboard chipset then did some testing on prototype and team fortress 2  There was certainly some great slideshow action happening but it didn't crash like before.  A stranger occurrence is when I reboot into linux, compiz actually seemed to run *smoother* on that chipset than with the graphics card.  But anyways I cleaned the card put it back in and set a box fan in front of the computer while I stress tested it.  It didn't crash but it wasn't exactly smooth either.  It did seem to slow down when I turned the fan off though.  So it seems like a certainty it's the graphics card.  Unless something else is overheating.  Kinda sucks too because I preordered portal 2 just a day or two before it started doing this.

So my next question is what graphics cards would anyone suggest?

---

### Post by K_45 on 2011-04-13
What is your PSU brand and how many amps on the 12V rail(s)? Also, can you test the card in another PCI-E slot (if you have one).

---

### Post by GTMoraes on 2011-04-14
It's the Graphics Card or the PSU.
Considering you're on Windows, try playing a movie with wPrime running on the background and see if the computer dies. If positive, it's the PSU. Else, test with another graphics card or use the Onboard one (if available).
Remember your Onboard video doesn't drain that much power, compared to a add-on videocard

Good luck =)

[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by .mouse on 2011-04-15
> **K_45 said:**
> What is your PSU brand and how many amps on the 12V rail(s)? Also, can you test the card in another PCI-E slot (if you have one).

I'm not sure what you mean by rails but the specs are here.
[http://www.hp.com/large/campaigns/personal_again/datasheets/HPPavilionVerdeSEa6645fPCDatasheet.pdf](http://www.hp.com/large/campaigns/personal_again/datasheets/HPPavilionVerdeSEa6645fPCDatasheet.pdf)
If that's not enough information let me know.


> **GTMoraes said:**
> It's the Graphics Card or the PSU.
Considering you're on Windows, try playing a movie with wPrime running on the background and see if the computer dies. If positive, it's the PSU. Else, test with another graphics card or use the Onboard one (if available).
Remember your Onboard video doesn't drain that much power, compared to a add-on videocard

Good luck =)

[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE=1]**Ubuntu Powered.**[/SIZE][/CENTER]


I'm only on windows when I'm playing a game.  The rest of the time I'm on linux.  :D
What's wPrime though?

---

