---
title: "dv9500 laptop speakers pop constantly"
date: 2009-11-04
forum: Hardware
---

### Post by Jessicaski on 2009-11-04
I have a HP Pavilion Entertainment pc (dv9500) and today I switched to ubuntu (I believe I have the newest version, 9.10).  I had been using vista on the ;aptop for a couple years, and partitioned the computer so that I can run both Windows and ubuntu.

But since the installation started and even now that it is done, the speakers keep making popping noises even when muted.  A soft popping noise will start followed by a louder one 3 seconds later.  After ten seconds the soft pop happens again.  I have tried switching to headphones and separate speakers and I normally use a docking station with its own speaker which it is hooked up into now. 

I think it probably needs the driver updated but I can't find a driver for this that will work in ubuntu.

HELP!

---

### Post by TroyDowling on 2009-11-05
Hey Jessica,

I ran into the same problem on my HP DV9000. It is very annoying! Fortunately there is a quick and easy solution. The reason this is happening is on account of a new update to the ALSA sound system. Simply follow the commands below to set it straight.

First, open up the run dialog by hitting Alt+F2

Type:
```

gksudo gedit /etc/modprobe.d/alsa-base.conf

```

This will bring up that file in a text editor. Ctrl+F to search for "power_save" and it should find a string that reads "power_saver = 10". Simply change this to "power_saver = 0" and save the file. When you reboot the problem is solved!

Hope this works for you,
Troy.

---

### Post by SilverCode on 2009-11-05
I'm having exactly the same problem on my HP dv9000 with both Ubuntu 9.10 and Kubuntu 9.10. I don't have this problem in Kubuntu 9.04 though.

---

### Post by SilverCode on 2009-11-05
TroyDowling fix above seems to have worked. Thanks!

---

### Post by Darkz_Soul on 2009-11-28
Awesome that worked great! fixed it instantly on my dv6663us, i think this has to do with the model of speakers that these laptops use and drivers that are not quite built for them, thanks

---

### Post by CuriousSoul on 2009-12-23
Solved the same problem on my HP dv6137. Thanks alot! :P

---

### Post by gohsthb on 2010-01-17
It sounded like the sound kept turning on and off.  Every time a sound would play I would get a pop just before I heard the sound.  So the sound card must have been going to sleep and when it would wake up would cause the pop.  With any continous sound, i.e. listening to Internet radio. I would get just one pop at the start and that was it.  This has happened on any computer I have put 9.10 on.
This fix has worked for me, thanks.

---

### Post by thecaptainzap on 2010-01-27
I've got a HP Pavilion dv6000 and this fixed my problem. Thanks a bunch!

---

### Post by AlexZaim on 2010-01-27
@TroyDowling What does the change involve? What is the variable for? Does it concern only the speakers or something else?

---

### Post by Ayuthia on 2010-01-27
> **AlexZaim said:**
> @TroyDowling What does the change involve? What is the variable for? Does it concern only the speakers or something else?

It is a setting for the speakers.  The power saving feature is turned on for the speakers and the popping noise you hear is when the speakers are turned off.  The speakers turn off after the specified time of inactivity.  If it is at zero, it does not turn off.

---

### Post by gsparky2004 on 2010-02-19
This also worked for my Compaq Presario C500 running Ubuntu 9.10 (Karmic).  I also had the annoying popping sound, but after my speakers "powered down", they would begin spewing out all kinds of electronic garbage.  I could tell when my hard drive was being accessed, the sound of my fan kicking on was magnified, and when my CPU had serious number-crunching, I could tell.  Plus, I could hear the static created from my wireless.  

My guess?  When the speakers are powered down, they're left in some kind of electrical floating condition that makes them ripe to pick up all of the stray electromagnetics going on inside the system.  So, if you (like me) have had problems with stray speaker noise, try TroyDowling's solution.

And thanks, TroyDowling!

---

### Post by tdmsbn on 2010-02-21
Thanks a lot for this fix, you have no idea how annoying it is to have you speakers pop like crazy even when they are muted. Awesome job, thanks for the fix.

---

### Post by tommynz1975 on 2010-03-21
Thank you

I am hopefull for this to work

I was afraid it was a power issue and the lappy was gonna fry.

This is on a Packard Bell easynote.

---

### Post by soulspit on 2010-04-02
!!

I didn't even realize it, but this popping has been subliminally driving me nuts for the past month since I installed Kubuntu, and I only just today noticed how aggravating it was, and thought "this never happened on Windows, surely it can be fixed."  And this thread is the first result I got in google.  My stress level will be permanently if imperceptibly reduced.  Thank you!

---

### Post by ArtichokU on 2010-04-28
i have a hp dv6227cl > unfortunately, this didn't work :/

---

### Post by schnide on 2010-05-02
Hi there, I have a HP Pavilion DV7 but the popping only happens when I start trying to play something. 

I tried the fix, however there was no "power_save" listed in the file. I'm still pretty new to ubuntu so any help would be greatly appreciated!!!!

Thanks, Jake

---

