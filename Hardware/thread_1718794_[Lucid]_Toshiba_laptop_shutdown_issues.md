---
title: "[Lucid] Toshiba laptop shutdown issues"
date: 2011-03-31
forum: Hardware
---

### Post by cupoange on 2011-03-31
Been running ubuntu just fine on my laptop for about 3 years.  I am on the Lucid, and have had no problems since first day it was released.  Recently the laptop will not shutdown properly; it issues the halt and power down command and then just sits there.  Only way to get it to shut off is to hold power button in.  When I go to restart it (seemingly randomly), it won't start x and boots to terminal only.  Trying to start x fails.  If I leave the laptop off for a while and come back, it usually boots up normally.  It will run fine without any problems til I try to shut it down again.  

I've checked xorg logs, syslogs, and just cannot discern what is going wrong.  I thought maybe it was overheating, so I reapplied fresh thermal paste and reseated the heat sink.  The good thing is it seems like it is running cooler than before, but the problem above persists.  Before I save everything and rebuild the machine, any suggestions??

---

### Post by Bartender on 2011-04-04
I'm having similar, but not identical, problems with an Acer 5920.  It's been running 10.04 for a few months now, and two or three other versions of Ubuntu previously.  Just recently I started having shutdown problems.

The purple "ubuntu" splash screen comes up, the little dots tick toward the right, but the dots stop changing color at either the last or second to last one.  The fan spins down, then the laptop sits there for two or three minutes before finally shutting down completely.  If I press the power button when it's stalled the laptop finishes shutdown immediately, not after a delay.

It starts back up like nothing's wrong.

I've noticed that if I start the laptop, then shut it right back down again, it will turn itself off like it should.  It appears that if I open any applications, then close them, the laptop hangs.

Recently I've been running the laptop on AC with the battery removed sometimes, and with the battery plugged in at other times.  I don't know if that could confuse the shutdown process somehow?  It seems that the shutdown problems started at about the same time.  It'll hang with or without the battery, so I don't know if that has anything to do with it...

---

### Post by cupoange on 2011-04-06
UPDATE: Upgrade to Natty Beta and the problem persists.  Seems related to amount of time laptop is on.  Possible overheating issue.  After letting the laptop cool for a while, boots fine and operates normally.

Now I'm having an issue that the touchpad stops working randomly.  Not sure if it's related or if it is a bug in Natty Beta.

---

