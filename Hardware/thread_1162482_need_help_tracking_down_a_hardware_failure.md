---
title: "need help tracking down a hardware failure"
date: 2009-05-17
forum: Hardware
---

### Post by jimmy the saint on 2009-05-17
I have a Dell Insprion 600m that I absolutely loved to use.  Unfortunately, within months of the warranty expiring (of course) the laptop crapped out on me.  I am not 100% sure what exactly failed, so I will lay out the symptoms and maybe you can help me track the faulty bit down.  

The laptop will boot up just fine (usually) but then it will freeze.  A hard lockup.  I have to do a hard shutdown every time.  That happens in windows, and linux.  Installed OS and a boot cd.  It takes between 1 and 3 minutes to lock up.  

What I tried:
Removing the RAM sticks one at a time.  
Applying new thermal goop the proc/heatsink.
cleaning, checking the fans.

I am at a loss.  It could be any number of components, but being a laptop, it is difficult to test individually.  I am sure there are log files that could be useful, but I have no idea which ones to look at.  Any help would be appreciated.  

Thanks, 

JTS

---

### Post by Joeb454 on 2009-05-17
It *could* be a faulty connection somewhere, I would suggest checking that also :)

Make sure there's no loose objects around the motherboard that could be shorting it or clogging anything etc.

Other than that I don't really know what to suggest, it could be a faulty CPU or motherboard, but they're very awkward to test, and we'll remain optimistic for now :D

---

### Post by mustangzach on 2009-05-18
I had a computer that would do that if two channels on the IDE controller were being accessed. Weird, eh?

Try something like a USB boot or something. Avoid the IDE channels.

Also, my server was really weird. If I had just one RAM card in, it'd run fine. But if I boosted it to 256MB RAM, it'd crash upon loading the X server. Er.. or it may have been if I logged in from GDM, I can't remember correctly. Just general weirdness. It had integrated graphics, but I put an NVidia MX4000 I had laying around (I know, overkill on an old Celeron, but it's all I had) in it, the RAM would work. The CLI worked fine, I could have used that I guess, but I like to browse the internet on it sometimes lol.. I needed X.

Just try checking all the caps on the board. That's a common problem with motherboards, sounds like the problem you're having.


-Zach

---

### Post by jimmy the saint on 2009-05-18
Hey thanks for the tips.  Are there any specific log files that may be useful?

---

### Post by mrtomservo on 2009-05-18
If the bios has an option to check the hard drive, I would.  You might also be able to download software from the hard drive manufacturer to do a check as well.  Then boot off a live CD and try a memory test, and let it run for a while, see if it crashes.

If you're having hard lockups you probably won't find much useful info in the logs. :(

Maybe you're laptop is warming up and expanding and pulling on a weak soldier joint or something.  If you have lm-sensors installed, maybe you should log your thermal zone temps to a text file and see if it's temperature related.

Best of luck!

---

### Post by Don Bowen on 2010-01-17
well NO, if you're running a 600m, and you install 9.10, it will freeze.  it will boot just fine, but if you run some other program, it freezes so that you have to hold down the power button to reboot.

I'm not the only one... and no one has offered a fix for this combo of machine and Ubuntu ... not that I've found yet.

9.04, I'm told, works, so I'm downgrading.... Maybe I'll have better luck with the next version change!

---

