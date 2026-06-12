---
title: "Ubuntu, Hibernate/Suspend and a broken BIOS?"
date: 2008-07-25
forum: General Help
---

### Post by The Tronyx on 2008-07-25
Hi Everyone,

I have somewhat of a Frankenstein computer based off of an e-machine and it has an integrated video card (Radeon xpress perhaps?) on the motherboard, a 200 gig HD, a 40 gig HD and an ATI x1600 pro (which I added).

The short version:  Had one install, it worked fine.  Did a clean install, it worked fine.  I went to work and when I came back it may have went into hibernation and done something to the BIOS/video card.  If you care to help, please read on =]

For around 2 years I kept my Linux install(s) on the 40 gig and used the 200 gig as a Windows partition and a place to store MP3s.  Later last night I decided that I would much rather have the space and decided to back the data up and completely format the 200 gig HD and install Ubuntu 8.04 on it.  This went fairly well and no major issues came up, my main goal was to get my ATI drivers working and dual-monitors set back up.  After I got that done, I went to bed.  When I went to sleep I turned off both of my monitors and when I woke up, powered them back on, wiggled the mouse and checked my feeds before heading to work.

When I got home from work the problem(s) started.  I turned on both of my monitors and wiggled the mouse only my computer never resumed its state, it just sat there not turning on the monitors.  Eventually I saw no way around this other than to manually power down the computer and reboot only this did little to fix the problem.  While having both monitors plugged into the ATI card (not the integrated) they never detected any video or never displayed anything.  The problem I am having is very very similar to this one [http://ubuntuforums.org/showthread.php?t=719789](http://ubuntuforums.org/showthread.php?t=719789) only I did everything he did and nothing worked (I also unplugged the power source from my computer for around 30 minutes).  The biggest similarity is that when I tried to boot the first time (and multiple times after) I got nothing other than a black screen and it wasn't until I connected a monitor to the integrated video that I got any display at all.  I also held down the insert key during boot which is apparently supposed to restore the BIOS to its defaults and while it would appear that it did this, before resetting I took out the ATI card and connected 1 monitor to the onboard. This presents another symptom, when using the onboard for video, the display is very very wobbly rendering the bios menu virtually unreadable.


Other Interesting symptoms:
-When the monitors are unplugged they say "Check connection" (or something) but when they are plugged INTO the card when the computer is on they say (entering power saving mode" (or something similar)
-If I do manage to get Ubuntu to boot with the integrated video, plugging the monitor into the card AFTER boot produces no video.
-While the only time I can get video is connected to the integrated card, it doesn't always detect the monitor/give any output

To be honest I am incredibly out of ideas so pretty much any rational suggestions would be greatly appreciated.  Thanks ahead of time for your assistance!

---

### Post by bigonegotaway on 2008-07-25
Had almost the identical situation. I was using Windoze and the power feature put the 'puter in power saviing mode-monitor off in 5 min. and HDD off in 10 min. Left the house for approx. 2 hours, came back and nothing. Tried all the usual resets, f8's f9's, f10's you name it, I tried it. The GOOD was the HDD was ok, the BAD was the the BIOS wouldn't even allow the FDD to be seen, the UGLY was my mobo and or BIOS chip had taken a dump requiring a mobo/BIOS change. Could have probably gotten a replacement BIOS from [www.biosman.com](www.biosman.com) for around $30 but that would still have left the possible bad mobo. Whole ordeal-new mobo set me back about $70-not too bad. I just couldn't get my head around the fact the 1 year old Asus mobo took a dump while in power saving mode. Oh well, hope this helps-good luck!

---

### Post by The Tronyx on 2008-07-25
Well....hmmmm...

I had hoped there would be a way to remedy this that wouldn't cost money but perhaps the BIOS is just toast.

Not that I doubt you or your answer but do we know why this happened?  What is it about suspend/hibernate that caused problems with the BIOS?

---

### Post by The Tronyx on 2008-07-25
Bump.

Anyone have any other opinions/suggestions?

---

### Post by bigonegotaway on 2008-07-25
You know, I feel it was just something that happened to occur when in the power saving mode. When I built my 'puter and then talked to a couple of people that were much more knowledgeable than I, they both sorta rolled their eyes when I told them what mother board I'd used. It was an Asus 
P4800-SX and after the fact research, exposed a peculiar problem with that mobo/bios combo. To repeat myself, I didn't go into hibernate, just power down after a time on the HDD and monitor. Also I forgot to mention that in trouble shooting I was never able to get any beep codes on boot attempt. A very good indication the BIOS may be bad. Look at the bright side-if it is the mobo/bios you get an excuse to do an upgrade ...heee...heee.

---

### Post by The Tronyx on 2008-07-25
> **bigonegotaway said:**
> You know, I feel it was just something that happened to occur when in the power saving mode. When I built my 'puter and then talked to a couple of people that were much more knowledgeable than I, they both sorta rolled their eyes when I told them what mother board I'd used. It was an Asus 
P4800-SX and after the fact research, exposed a peculiar problem with that mobo/bios combo. To repeat myself, I didn't go into hibernate, just power down after a time on the HDD and monitor. Also I forgot to mention that in trouble shooting I was never able to get any beep codes on boot attempt. A very good indication the BIOS may be bad. Look at the bright side-if it is the mobo/bios you get an excuse to do an upgrade ...heee...heee.

It will/can be made to boot when the monitor is hooked up to the onboard video but the display is obscenely wobbly (not far from completely illegible).  When a monitor is plugged into the video card it doesn't boot or make noises or really sound like it is doing much of anything.

I am going to be doing some troubleshooting tonight but first thing in the morning I am going to pick up a power supply and see what that does.  I know that when a power supply starts to go, very strange things can happen.  I guess if it isn't the power supply the only real cost is a few minutes of travel to return it =]

---

### Post by The Tronyx on 2008-07-26
Well just a small update.  The power supply didn't change anything so it looks like the motherboard.

---

