---
title: "Is my Acer Aspire 5515 Dying?"
date: 2010-05-21
forum: Hardware
---

### Post by Stigmata13 on 2010-05-21
Hello. I'm having a lot of trouble with my Acer Aspire 5515.
I have had Ubuntu 8.04 LTS installed on it, so I could use ATI's proprietary drivers. It worked well for about a week, but now I'm getting some strange problems. Here's what happened:

I rebooted my computer. As it came on, it would pass post, and then show the Ubuntu logo. It would load, but right after it finished, it would show a black screen with a single white blinking thing in the upper left corner.
Then, it would just completely shut off altogether. Upon reboot, it would just get stuck in post. Disabling the quiet boot, I found that the last message it would give would be a message saying "Fixed WDC............) the ...... being numbers of the drive, can't exactly remember.

Anyway, the only way I am able to boot into Ubuntu at all is either to run the recovery tool, and reconfigure xorg, of which it will work properly until i decide to shut down or reboot.

Or, After trying to boot once, "hot killing" it while it is stuck at post, and then booting normally, it gives me an error and loads up in low graphics mode.

I've seen this happen to quite a lot of computers before. Is my graphics chip dying? I'm really worried because this is a laptop and you can't just stick a new video card in it.

---

### Post by wilee-nilee on 2010-05-21
I would download a live cd and see how it runs from a cd, it may just be the operating system is borked. I don't think anybody on the forum is going to be able to give you a definitive answer as far as the hardware goes.

Put the Live ISO on a thumb with the startup disk creator with some persistence so that you can run it more then once to confirm the hardware is okay.

---

### Post by Stigmata13 on 2010-05-21
Thanks... I tried the Live CD, it works fine, the resolution loads up correctly and everything.
The only thing I noticed, is I cannot 'restart' my computer, I have to shut it down, because if I restart it, it gets stuck in POST and won't load.
At first I was worried, because I'm very computer literate (I went to a vocational school for Information Systems Technology for two years) and I know a lot of the time the first thing to go is the graphics chip/card.
But after doing a fresh install, it seems the restricted driver Ubuntu offers works correctly, aside from the POST incident which occurs.
Although I really can't understand why the ATI driver that was working previously no longer works, even under a fresh install.
Do you think it could be the BIOS?

Edit: On a side note, on boot I always get an error:**MP-BIOS bug ****timer not connected to IO-APIC **for a second before boot, but that happened previously and it never seemed to cause any problems.

---

### Post by wilee-nilee on 2010-05-21
In the terminal ```
lspci | grep VGA
``` 
you might want to use this ppa it has updated drivers.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)
I'm not sure about ATI, all my computers seem to run the graphics card or they just don't, IE the only problem I run into is screen resolutions.

So you did a fresh install from what I read what did you install?

The restart is a little strange I assume you know about the soft reboot or shutdown.
[http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub)

I'm not sure this helps but I have a acer aspire only 9 months old and I have lost the ethernet port, so I will send it in for repair on warranty. I think the acers in general don't cool correctly, or the fan passages are just not setup correctly. The atom chip in mine is [http://en.wikipedia.org/wiki/Reisubsupposed](http://en.wikipedia.org/wiki/Reisubsupposed) to run cooler but I suspect it still gets hot, I have no way of reading the temp or fan speeds.

---

### Post by Stigmata13 on 2010-05-21
Running that command, I get the following output:
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
I installed 8.04 LTS, I did so because my graphics chip was put on legacy, and anything further past 8.10, I could not use proprietary drivers.
One thing I noticed... running the live cd, even though everything worked, the graphics chip was not being shown under the restricted hardware drivers.
Previously, it would be shown. (I have booted to a Live CD several times before, to resize partitons, for example.) But my installation sees it right now, and I am able to enable "extra" desktop effects using the proprietary driver suggested by Ubuntu.

By the way, the thing that got me most worried was the lockup in POST. A systems OS shouldn't cause a lockup in POST, should it?

---

### Post by wilee-nilee on 2010-05-21
> **Stigmata13 said:**
> Running that command, I get the following output:
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
I installed 8.04 LTS, I did so because my graphics chip was put on legacy, and anything further past 8.10, I could not use proprietary drivers.
One thing I noticed... running the live cd, even though everything worked, the graphics chip was not being shown under the restricted hardware drivers.
Previously, it would be shown. (I have booted to a Live CD several times before, to resize partitons, for example.) But my installation sees it right now, and I am able to enable "extra" desktop effects using the proprietary driver suggested by Ubuntu.

By the way, the thing that got me most worried was the lockup in POST. A systems OS shouldn't cause a lockup in POST, should it?

By post do you mean shutdown or reboot I'm not familiar with all the nomenclature, being a armchair user. Should start and shutdown in a normal amount of time maybe somebody else will have better idea. You just might want to confirm the OS install so there is information available. If it locks up with the cd I have had that happen periodically, I just use a thumb drive nowadays, and have no problems.

Here is link to a google search with your card and Ubuntu.
[http://www.google.com/#hl=en&source=hp&q=VGA+compatible+controller%3A+ATI+Technologies+Inc+RS690M+](http://www.google.com/#hl=en&source=hp&q=VGA+compatible+controller%3A+ATI+Technologies+Inc+RS690M+)[Radeon+X1200+Series]+ubuntu&aq=f&aqi=&aql=&oq=&gs_rfai=CESIYl1r2S4OjDoiOoATVxcCPAgAAAKoEBU_QK8M-&fp=119c5f3496e7bdc2

I think there are just problems in general with older cards, but a person would think that a computer only a couple of years old would not have problems. But it's not as if the card manufacturers are presenting open source drivers. So it seems that there are bugs with xorg but I think it's more the developers trying to reverse set up drivers, we can only expect so much I guess.

Oh I see POST means power on self test, hmm I don't know I guess I would look in the bios and see if there is a quick boot that can be disabled to see if it changes, but I am just guessing here like almost always anyways.

---

### Post by Stigmata13 on 2010-05-21
Alright, thank you :)
My system seems to be running normally, I was afraid the hardware might have become damaged but it appears everything is working fine.
Thank you for the help, kudos to you! =D>

---

### Post by wilee-nilee on 2010-05-21
> **Stigmata13 said:**
> Alright, thank you :)
My system seems to be running normally, I was afraid the hardware might have become damaged but it appears everything is working fine.
Thank you for the help, kudos to you! =D>

I like my little acer netbook I had W7, Lucid and XP, and arch and a couple of other distros in sun virtual on it and it ran great with a 2 gig memory, but I had to buy the OEM discs to reinstall XP to get them to repair it. The XP I had wasn't the OEM.

---

