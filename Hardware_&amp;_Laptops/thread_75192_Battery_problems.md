---
title: "Battery problems"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by aburda on 2005-10-13
Hello,

        My laptop battery recently died on me (the laptop is a two year old toshiba satellite A10 so this is to be expected).  I ordered a new battery and I still have the same problem, i.e. if I disconnect from the power adapter the system loses all power immediately and shuts off.  I suspect that I may not actually have a battery problem but that there is something wrong with the circuitry that is responsible for recharging the battery.  Both in windows and in Ubuntu it says the battery is fully charged.  Any ideas where I should start looking? If I'm going to fix it I figure I'll have to start playing with ACPI and force it to charge, but I don't have a clue where to start.
       Additionally, just to make sure I'm not overlooking anything, the new battery I bought is 10.8 volts as is the original but has 4400mAh (the old one had 3600).  From my understanding this just means the new battery can carry more charge, not that it is incompatible with the system.  The batteries look identical and the new one has the same physical interface.  When hunting online for the part number several sites recommended this new part number

          Thanks,

          Aaron

---

### Post by skirkpatrick on 2005-10-13
Yeah, your new battery just has more capacity.  Unless your DSDT is working flawlessly, Linux will incorrectly report your capacity.  Since Windows is also incorrectly reporting it, it sounds like there's a problem in your system.  Does your battery have a button and LED readout so that you can check its capacity?

According to the SMBus spec, if the battery isn't actually talking to your laptop, Windows (or Linux) shouldn't even tell you there is a battery present.  If it's not charging and is actually dead, they should report it as 0% capacity if they can actually talk to it.

---

### Post by aburda on 2005-10-13
Skirkpatrick,

     As always, thanks for the reply, I was reading about DSDT but for now would just like to get to the point where I can pull out my power cable and not have the system die.  Presumably the DSDT is configured to monitor there being at least some charge (at least it was working before with the old battery until it died).
     Under windows if I go to control panel and click on 'power options' and the look at the battery I can get the unique ID, etc.  If I then shutdown, swap batteries and reboot, windows has found that the battery has a new unique ID  so there is definitely some communication going on with the battery.  Presumably the same in Linux, as mentioned both OS's think that the battery is fully charged.  But without the power cable plugged in I can't even turn the computer on to get to the CMOS/boot selection process.  Thinking about this, perhaps there is a short somewhere in the laptop?  The communication works but not the actual power supply?  

          Aaron

---

### Post by skirkpatrick on 2005-10-13
Either a short in the laptop or maybe the communication pins are making contact but not the power pins.

---

### Post by aburda on 2005-10-13
I can't imagine that it is the communications pins making contact but not the power pins as I have two batteries and neither works, unless the pins in the laptop somehow got bent, which I think is quite unlikely.  Its looking more and more like a short....any recommendations besides either putting up with a laptop that doesn't have a battery or buying a new one?

     Aaron

---

### Post by skirkpatrick on 2005-10-13
What did Windows say about your old battery?  There's a possiblity that it's something as simple as a blown diode or fuse that's preventing the laptop from drawing power from the battery (fuse is very likely).  You'll have to open your laptop to check but it's not like it's under warranty anyway.

Googling around doesn't seem to turn up anything relevant.

---

### Post by orvillle on 2005-10-21
Hi Aaron

I've been searching for information on this problem too.  I replaced my battery a month ago and it was charging ok and running the laptop (Toshiba Satellite S1900, Windows 2K).  A week ago my screen suddenly went dark - could see the desktop images only with a light held in front, so figured it could be the backlight or the inverter.  Replaced the inverter as that was easiest to try first, but no difference, waiting for a new ccfl. 
I've noticed now that the battery is constantly "charging" under AC power although is always registering at 92% charged and if the AC is disconnected, the laptop immediately switches off.  My original battery doesn't boot up either, but it was always a bit iffy so can't read too much into that.  Any ideas - I know you were discussing the possiblity of a blown fuse in your laptop - have you found the answer yet?

thanks

---

### Post by BungaMan on 2007-04-13
I know its an old thread but there's no answer to this and it shows much similarity to my issue(s).  Did anyone find a solution?

---

