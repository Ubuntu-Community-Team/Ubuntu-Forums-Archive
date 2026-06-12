---
title: "ML3109 on xubuntu 9.04 suspend does not work"
date: 2009-07-26
forum: Hardware
---

### Post by zemoffm on 2009-07-26
Hey everyone,

I recently "upgraded" from ubuntu 8.10 to xubuntu 9.04 on my Gateway ML3109 laptop.  For those of you who don't know, its a 2 year old laptop that has a celeron m processor, and is basically a budget laptop, although I upgraded the ram to 1.5 gigs.

Anyway, Ubuntu 8.10 worked fine on it, with ati fglrx drivers and everything pretty much right out of the box, suspend support included.  I wanted a lighter desktop and thought I'd upgrade to xubuntu 9.04.  

So now I have xubuntu 9.04 running on my laptop, but noticed that first of all, fglrx driver does not work on my laptop (guess they discontinued support for it).  No problem, I don't really use the 3D capabilities anyway.  But, the problem now is that suspend does not work.  It goes into suspend just find, but when I try to come back from suspend, the display does not turn on.  I am using the default radeon drivers, and think it might have something to do with that since the computer seems to be running (fans going, HD light comes on for a bit, that sort of thing).  Anyone have any experience with this sort of thing?  I would like suspend to work as I use it pretty frequently on my laptop.  I have fully upgraded to the latest kernel and radeon drivers from the repository.

While I'm at it, my Fn volume keys always worked in ubuntu 8.10, accompanied by a nice little Mac-like volume overlay on the screen.  In xubuntu 9.04, they no longer control the volume mixer, and nothing pops up on screen showing that they are working.  Is this an xubuntu vs ubuntu thing, or just something that changed under the hood between 8.10 and 9.04.  My volume works fine, its just a hassle to always have to open up the mixer THEN change the volume.  Wish I could just use the Fn volume keys.  Something I need to install maybe?  On a side note, my Fn display brightness keys work just fine accompanied by the overlay on the screen, just like they did in 8.10.  On a side note, can someone explain why I have two sound cards appear in the mixer, HDA ATI SB (alsa mixer), and SigmaTel STAC9200 (oss mixer)?  I get that there are two different mixers, but why?  They both seem to work fine in terms of putting out sound, but just curious as to whats the point.

Anyway, if anyone has any ideas of where to start on these problems, it would be much appreciated!

Thanks in advance.

---

### Post by JonathanRRogers on 2010-04-20
The two different mixer devices are really the same one, accessed through different kernel interfaces (OSS and ALSA) and showing them both is redundant and confusing. Management of sound devices and integration with Pulseaudio is much improved in Karmic (9.10), but you may have trouble installing or using it. See my post in [http://ubuntuforums.org/showthread.p...62#post9150762](http://ubuntuforums.org/showthread.p...62#post9150762)

---

### Post by harrismh777 on 2010-04-28
hi dude,
I have the same problem with my HP s7400n slimline.  Asus PTGV-DM

The machine suspends, the power light (blue) turns yellow.  Pressing the power button to wake it up turns blue, disk light blinks, and then nothing.

The lan is not connected... I cannot ping the unit. Also, re-sourcing the display does not work. I have to power off hard.

Rats..    running Jaunty 9.04 with updates.  The machine has 512 Megs memory... and the intel chipset.

:(

---

### Post by lurgee on 2010-05-25
Similarish issue.  On a whim I suspended my Xubuntued laptop (eMachines E625) instead of powering off as I usually do.  When I brought it back, two things were apparent - it had decided to disconnect my internet (firefox was absolutely convinced there was no connection, until I physically clicked on the icon on the top right and told it to connect ... since then, no probs) and the display is stuck on low power mode, as if the laptop thinks it is running on battery.

My hunch - based on zero expertise - is that this is a check box issue - suspending has put a tick (or removed a tick) somewhere, just as happened with the internet connection.  But I'm darned if I can work out where.  Looking through Settings Manager doesn't throw up anything that looks unusal or wrong.

Suggestions?  Preferably in straightforward English - assume you're talking to an idiot.

---

### Post by lurgee on 2010-05-26
My issue around brightness was resolved when I downloaded Power Manager from the software centre. A s soon as I opened the programme - without me having to do anything more - the whole darn monitor lit up like a Christmas tree.  Hadn't realised how used I'd got to dim grey.  Obviosuly, that's no help to anyone else, and probably not a fix even on my problem, but now i've got it sorted I'll just steer clear of the jinxed Suspend button.

---

