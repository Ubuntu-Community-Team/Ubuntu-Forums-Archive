---
title: "laptop battery life question"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by tim202 on 2007-09-07
Hey guys.  Here's my dilemma:
I have  a Toshiba A105-S2091 laptop, which runs a Celeron M 390 processor, with Feisty installed.  Everything really works great, or at least I thought I did, until I started reading about this whole CPU throttling thing.  See, this laptop takes an hour to charge and dies in about an hour and fifteen minutes, which totally sucks because I take it to school with me to do work on and I have to search around for a chair next to a wall outlet every time I need to use it.

Heres the thing though:  After spending the better part of yesterday searching the forums and following every howto i could find, I've enabled the CPU frequency Applet thingy in Gnome, and it says the processor is running 1.69 Ghz, which is 100%.  When i hover over it, it says "CPU Frequency Scaling not Supported."  I'm running kernel 2.6.20-16-generic.

What I'd like to know is;
-Is it my kernel version that's holding me back?
-Does anyone know if the Celeron M 390 even supports frequency scaling?  There's nothing in the Bios that enables it.
-Should I consider downgrading to a previous version of Ubuntu?  I really need the battery life.

Thanks,
TIM

---

### Post by jnorthr on 2007-09-07
Whoa - Tim ! That battery life does suck. Have you considered putting a new one in just to boost battery life ? You've probably looked at system>preferences>power prefrences to set the display timeout as low as possible. Dunno if you system has a bios setting to reduce power on your disk drive as this is generally a much greater power drain on a system than the CPU and/or display. Keeping these setting as short as possible, say a few minutes for the display timeout, may just possibly give you a few more minutes of life than you have at the moment, but i would not expect it to be any great-leap-for-mankind kinda improvement. Sorry..

---

### Post by dasunst3r on 2007-09-07
I thought Celeron processors don't support speedstepping, but I may be wrong.  Try this: [http://ubuntuforums.org/showthread.php?t=190921](http://ubuntuforums.org/showthread.php?t=190921)

When people ask me for advice on what computer to buy, I tell them to avoid the Celeron processor like the plague.

---

### Post by DarkStarAeon on 2007-09-07
The Celeron M processor is known to drain a battery in no time flat. 

Unfortunately from experience, I can tell you that the Toshiba Satellite models with Celeron M processors in particular are notorious for their short battery life, and pretty much no matter what you do, it isn't going to help.

All you can really do is either buy a better battery, or, buy a solar recharger like this: [http://www.modernoutpost.com/gear/details/jv_powerdock_elite.html](http://www.modernoutpost.com/gear/details/jv_powerdock_elite.html)

---

### Post by tim202 on 2007-09-08
dasunst3r , thanks for the advice, i tried that howto and it worked.  My CPU isnt stuck at 100% anymore, and its looking like powernowd is working.  now to see if it actually affects battery life...  

and jnorthr, i plan on taking your advice about reducing power to the hard drive... but if there isnt any bios setting to reduce power, does anyone know if there is another way to do that, like maybe with an app or something?

thanks for the advice, everyone
TIM

---

### Post by jnorthr on 2007-09-08
Sorry, Tim. Don't know any app that would stop hard drive as that's a very low level activity. Another idea - any chance of carrying a 2nd fully charged battery for those intimate moments :rolleyes:

---

### Post by tim202 on 2007-09-12
Meh... another battery is way too expensive.  I have an accidental damage protection warranty on this laptop though.... and that LCD screen is starting to look like it might be comfortable to sit on.. accidentally...

But seriously tho... thanks everybody
TIM

---

### Post by DarkStarAeon on 2007-09-12
"accidentally"   lol ;)

Only other option I can think of is buying a solar charger, not the phone/ipod type, but the ones that can actually power a laptop. They basically look like a laptop bag, you open them up and inside is a bunch of solar cells. Some even will hold the laptop too.

They cost more than a laptop battery, but they are damn useful.

Just a though.

---

### Post by lisati on 2007-09-12
The A100-series Toshiba laptop I have (also with a Celeron M) came with Windows software preinstalled that is able to set processor frequency and other resource usage according to whether its running on battery  or AC...This included dimming the screen as required.

And I agree - the battery life seems to lack some "oomph" (45 minutes or so on my machine since installing Ubuntu, longer when new and running Windows)  I also recall reading something somewhere, possibly the Toshiba manuals that came with my machine, about larger capacity batteries - if I remember I'll get back to the team on that one.

---

