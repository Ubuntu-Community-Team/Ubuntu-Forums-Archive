---
title: "Upgrading to 8.10"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by Just-trevor on 2008-12-31
I have tried to upgrade to Intrepid three times now.
The first time it froze when the computer fell asleep and when I restarted the computer, the mouse and keyboard didn't work. Since this is a new hard drive and I didn't have anything I didn't want to lose on it yet, I just popped in the Hardy CD and erased the old one.  I would just use a CD to upgrade to Intrepid, but they won't work - the Hardy CD is actually one that came with The Official Ubuntu Book that I got for Christmas, and it is the only one that works.
The second time it froze after like 10 minutes when the computer fell asleep again, or I think that's what caused it, and when I restarted, it offered me a partial upgrade which I am counting as the third try.
The third time I figured that it was the computer going in to idle mode that caused it, so I set it to not ever turn the screen off, and set the computer idle mode to 2 hours, the longest it goes.  I would stay up the whole time and jiggle the mouse here and there while I read a book or something, but it was 3 o clock and I figured whatever maybe it will take less than 2 hours to upgrade.  When I got up this morning, I turned on the monitor and jiggled the mouse (this was at 11 or so, so it was going for 8 hours) and the screen remained black, with the indicator light thing orange.  I turned it off and back on, and it failed to load the kernel, but when I went to the Grub menu, all the options were 8.10, but all of them - recovery mode ones too - couldn't load the kernel, so I popped the Hardy CD back in - started over - and decided I'd ask you guys if you think  the problem is caused by the computer going idle, if I can change it to never go idle, or if you think the problem is something else, etc.  Oh and the third try, before I went to sleep, I rested The Official Ubuntu Book on the control key thinking that might keep it from going to sleep. I don't think any CD's I make will work - I've made like 4 already. I have considered using a USB flash drive, but I don't actually have one which is kind of a drawback.  Also my CD drive actually doesn't work - I have been using my sister's computer to put Hardy back on my computer - plugging the hard drive in to hers then putting it back into mine - because it is basically impossible to get the friggin CD drive out of there without using a hacksaw or something. Oh yeah and the Hardy CD is actually a Hardy DVD and her CD drive is actually a CD/DVD drive.
Any ideas?

---

### Post by lemming465 on 2009-01-01
Ubuntu 8.10 has a few unfortunate hardware regressions from 8.04, I'm sorry to say.  It sounds like you are tripping across them.  If you can get an 8.10 CD to boot using [kernel options ]("https://help.ubuntu.com/community/BootOptions") you might make headway.  One option is just to run 8.04 "hardy heron" for a while; it's supported until Fall 2009.

---

### Post by Just-trevor on 2009-01-02
Yeah, I figured I'd just run Hardy for a while longer too.
What exactly do you mean by "hardware regressions"?

---

### Post by lemming465 on 2009-01-03
> What exactly do you mean by "hardware regressions"?That hardware which used to work, stopped or got flakey or lost features. 8.10 has issues with ATI video chips, Nvidia video chips, and Atheros wireless chips compared to 8.04, just to name 3 I've run into personally.  Which is not to say it's terrible; I like it well enough that I upgraded a laptop to the beta and a desktop to the release candidate before it was even officially out.  However, I have enough Linux experience (since 1993 and kernel 0.99 :-) to cope when minor things broke, though my rate of bug reporting in launchpad took a big jump.

In general, it seems to take Ubuntu about a month after release to fully stabilize.  However, the Hardy -> Intrepid transition had an above average amount of breakage, compared to every other version I've run (starting with 5.10 Breezy Badger).

---

### Post by Pumalite on 2009-01-03
Try a Live CD and see if it's compatible with your hardware and see if you like it.

---

### Post by Just-trevor on 2009-01-04
Pumalite - I don't really have the means to make a working Live CD - I mentioned above that I've made like four already
Lemming - oh, ok
I guess I'll just wait a bit
I actually do have a pretty sucky video card - ATI Rage 128 Pro Ultra - and I wouldn't be surprised if it isn't supported with Intrepid cuz I've had issues with Hardy and Gutsy and Fiesty...
I think I'm going to get a better one with Christmas money or whatever and maybe I'll try to upgrade then.
I can't really think why my Live CD's haven't worked, though.  I made them on the family computer, the same computer and case of blank CD's that I made the Fiesty CD with, now that I think of it. Do you need better quality CD's or something now?

---

### Post by Sef on 2009-01-04
> One option is just to run 8.04 "hardy heron" for a while; it's supported until Fall 2009.

That is not correct.  It has Long Term Support, so desktop support will run until April 2011.  The server support will run until April 2013.

---

### Post by Pumalite on 2009-01-04
'Do you need better quality CD's or something now?'
Make it the best you can get

---

### Post by Just-trevor on 2009-03-11
OK, so I erased my old stuff and started over completely with a new fresh installation, but it's still the same - freezing every 4 minutes - LAME
I only just now thought of the keyboard lights - the second and third ones, caps lock and scroll lock, flash on and off when it freezes.  Also sometimes it even freezes on startup, and since I don't have a splash screen, I see that it says kernel panic, flashing the lights on the keyboard.  What do the lights mean? I don't think it is a problem with the installation, because when I was installing it, I had to keep reinstalling because whenever I tried to update - there are 261 updates - it freezes when upgrading the kernel, every single time (except the latest time because I haven't updated for fear of having to start over again) and when I try to restart it doesn't work, in which case I popped the live cd back in and reinstalled again...
What's wrong?

---

