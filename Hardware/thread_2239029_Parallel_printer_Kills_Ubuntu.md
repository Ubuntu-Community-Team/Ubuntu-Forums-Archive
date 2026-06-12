---
title: "Parallel printer Kills Ubuntu"
date: 2014-08-11
forum: Hardware
---

### Post by rbmoler on 2014-08-11
I switched to Ubuntu 12.04 early this year.  Although I have a network for my family and there are two printers on the network, I kept an old Samsung 1750 connected to my parallel port for my immediate use.  I had no trouble getting it installed and it worked just fine until recently.  I believe it was just after I was told to replace the drivers because the old set was going out of support.  Some time later I wanted to print an email and things went south in a hurry.  Not only did it not print (the printer came on then turned off a bit later), but the screen went crazy (purple vertical stripes) and I had to reboot.  This occurred several times afterwards.  Today I decided to delete the printer and reinstall it. The re-installation seemed to proceed normally.  When I tried to print a test page the same issue occurred - the screen went black this time and nothing worked.  I rebooted and noted that a brief message appear indicating a "broken pipe".

Perhaps my old printer is no longer supported.  A newer Samsung printer on the network works just fine when I print to it.  So it's just the old parallel printer or the parallel port or the new drivers that are at fault.

Any ideas or suggestions?

---

### Post by Vladlenin5000 on 2014-08-12
The "broken pipe" error message suggests a problem with the graphical drivers and the symptom is also consistent with that.
What is is graphics card/chip and what driver are you using?

---

### Post by coffeecat on 2014-08-12
From what Vladlenin5000 has said, it appears you have two problems. But I am puzzled by this:

> **rbmoler said:**
> I believe it was just after I was told to replace the drivers because the old set was going out of support. 

Which drivers? Who told you this? If your printer is the Samsung ML-1750 it is still listed as being supported in 14.04. Any cups driver updates would normally come through the update manager.

---

### Post by rbmoler on 2014-08-12
I only do updates through the updates manager.  The last two times I received an update notification through the update manager it listed several updates which I allowed to be done.  It also had a notification at the top, in a separate box, regarding a driver package (I think, because my memory is a little vague about the actual wording.)  It did say explicitly that the package I was using in my version of 12.04 LTS was going out of support on August 6th (or thereabouts) and that a new version was available to download and apply and gave an option to do so.  The first time I said to proceed with the update it failed with a message saying that something was missing.  (I'm going to have to learn to be more alert and record any such messages.)  The next time the update managed alerted me to some updates that I needed to apply the same separate driver update message appeared in a separate box at the top just like before.  This time when I allowed it to update it was successful.  It was after that that the Samsung printer started to act the way I reported above.  Nothing else seems to be amiss.  I can print to both my Brother and the newer Samsung printers that are on the network.  BTW, when the test print failed and I rebooted, the Samsung 1750 did not show up as an installed printer.

This computer is dual booted with Win XP so I booted into that this morning and did a test print which worked fine.  I'm writing this in XP at the moment. 

Regarding the graphics:  I have an ASRock 800GM-LE FX whose built in graphics is all the graphics I'm using.  There is no separate graphics card.  The default resolution is 1600 x 1200

---

### Post by coffeecat on 2014-08-12
The messages you saw are not familiar to me, but I haven't used 12.04 for some time.

I'm going to suggest something for you to do which may give you food for thought. I'm not suggesting you re-install - your problems may be fixable, but I have no coherent ideas at the moment - but you may wish to after this experiment.

Download the 14.04.1 ISO: [http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/) - and burn it to DVD or create a bootable USB drive if your computer supports booting from USB. Boot into the live desktop session, not the installer, plug in and switch on your Samsung printer and see if you can install it with the GUI utility. Now test printing from the Samsung and anything else you might want to test. It would be interesting to see if the Samsung printer works OK with this later version of Ubuntu, at least in its default 14.04.1 point release state.

Googling your motherboard - google went for 880GM-LE FX rather than 800GM-LE FX - suggests your motherboard graphics is Integrated AMD Radeon HD 4250 which should work OK with the default radeon driver in both 12.04 and 14.04.

---

### Post by rbmoler on 2014-08-12
The MB is the 880 version.  A typo on my part.

I've actually already (over the last 5 hours) upgraded to 14.04 through the update program.  Everything seems OK EXCEPT I don't have a thunderbird mail icon in the top right programs bar  I went to the software center and it said that Thunderbird was installed, but I can't access it. (I haven't tried using the terminal.  Maybe that would work.) That is a very big bummer, because I haven't a clue to what I should do about that.  It's far more serious than not getting the printer to work.  I should probably start a different thread for that problem. 

Ubuntu 14.04 is no better than 12.04 with the new drivers for working with the Samsung ML-1750.  The printer installer found it, went through the driver installation asked if I wanted to print a test page.  I did, the printer turned on, the screen turned blank white instead of black and I had to reboot.  It sure seems like there is something messed up with the drivers.  The printer can work through a USP port, so I'll try that next ,but that seems a forlorn hope.

---

### Post by rbmoler on 2014-08-12
OK, by golly I got everything to work.  There is something wrong with the parallel port interface or whatever, but it doesn't matter.  I switched to the printer's USB output, installed the printer and it worked fine.

I looked in my history and found the last time I had opened thunderbird, clicked it and thunderbird opened, the blue icon  at top right appeared, my old profile (on a separate HD) had been preserved and I'm now up and running except for a one program (glabel) that prints to DVD discs on my brother printer which I'll have to reload.

Case closed!

---

### Post by coffeecat on 2014-08-12
I'm glad it's all working now. It sounds as though possibly a hardware fault with the parallel port developed coincidentally with all those updates. 

For Thunderbird, if you open the dash and start typing thunderbird, you should be offered it after about "thu". Click the dash icon and it will open and a thunderbird icon will appear in the launcher. Right-click on the launcher icon -> Lock to Launcher, and then the launcher icon stays and you only have to click it once to open Thunderbird.

---

### Post by rbmoler on 2014-08-13
That's what I thought too - a hardware fault with the parallel port.  But when I booted to XP the printer worked, so it still looks like something fishy is happening with Ubuntu printing through a parallel port after the CUPS update, since it happened with 12.04 and 14.04.

Apparently the thunderbird  icon is already locked in.  It was present when I opened Ubuntu this morning.  So its odd disappearance was just a temporary glitch.  I didn't get any "lock to taskbar" when I went to dash and right clicked the thunderbird icon.

---

### Post by coffeecat on 2014-08-13
> **rbmoler said:**
> That's what I thought too - a hardware fault with the parallel port.  But when I booted to XP the printer worked, so it still looks like something fishy is happening with Ubuntu printing through a parallel port after the CUPS update, since it happened with 12.04 and 14.04.

Yes, of course. I  missed that it's still working with XP. I'd test this myself except that I long ago disposed of any printers and motherboards with parallel ports. I guess the problem may be that whatever updated driver or library has a bug in it affecting parallel printing, has been insufficiently tested because many of the testers don't have access to that sort of hardware any more.

---

