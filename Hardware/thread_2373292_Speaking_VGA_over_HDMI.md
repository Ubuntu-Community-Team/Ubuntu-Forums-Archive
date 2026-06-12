---
title: "Speaking VGA over HDMI?"
date: 2017-10-04
forum: Hardware
---

### Post by gmalecha on 2017-10-04
Hello --

I was trying to set up my laptop (Thinkpad X1 Carbon, Gen 4) to give a talk today and ran into something interesting. I directly connected the laptop to the HDMI cable, the monitor was detected, and I enabled it, but I only got a black screen (I tried unifying the outputs, dragging them over one another, switching my primary monitor, etc.). I tried again using a mini-display port to HDMI and plugged into my mini-display port with the same result, the monitor was detected, but the screen was black. As a last ditch effort someone got a small HDMI to VGA converter and plugged the laptop in through the laptop's HDMI port to a VGA connection to the projector. This, shockingly, worked and was a complete surprise to the other people in the room who said that the dongle couldn't possibly be doing the conversion. This got me thinking of another instance (completely different location) where, when connecting directly to HDMI I just got a black screen.

Has this happened to anyone else? Does anyone know of a way to solve this problem? Is it possible that the driver is "talking VGA" over an HDMI port (seems odd, but...)? Any insights would be greatly appreciated. I'm running Ubuntu 17.04 (installed via kubuntu) and my system is up to date.

---

### Post by TheFu on 2017-10-05
I use an HDMI-to-VGA converter for my presentations all the time.  The only tricks are to have the resolution and frequency setup to match whatever the projector can handle.  I use **lxrandr** for this.  Sometimes, I have to disable the output and re-enable it to get the projectors to "wake up."  In general, if you stay with the "hidef" TV standard resolutions and 60Hz, it just works.  Worst case, use 800x600 @ 60hz.

Of course, your HDMI connector/output could be broken. That could be on the laptop or the projector and any intermediate devices that the venue has between your connection and the projector.  Many have a way to record that output and those things don't always support the same resolutions that the projectors support.

---

### Post by Autodave on 2017-10-05
You may also have to have the HDMI cable and projector/monitor connected *before *you power up the PC.

---

### Post by gmalecha on 2017-10-05
My worry with using VGA is that I am finding that many places are moving to HDMI because they are moving from projectors to big TVs. I will have to try it again this weekend on my TV at home to see if I can re-produce the problem.

Thanks for the help thus far.

---

### Post by TheFu on 2017-10-05
> **gmalecha said:**
> My worry with using VGA is that I am finding that many places are moving to HDMI because they are moving from projectors to big TVs. I will have to try it again this weekend on my TV at home to see if I can re-produce the problem.

Thanks for the help thus far.

I give presentations almost every week.  In the least 4 yrs, only 1 location is still using VGA - after they'd assured me the location supported HDMI.  I'd been there before and we discovered that all other venues for that location had already moved to HDMI ------- except this single room.   

Fortunately, my presentations are pure HTML5, so a quick copy to flash and I could use the cough, cough, Windows presentation PC to do it.

Of course, the is a requirement to be prepared for anything when giving a presentation - perhaps it is time to get a chromebook?  They all have HDMI outputs and work pretty well.  Almost all will run Crouton and do not need a google account to be very useful - assuming you care about privacy.  Get a used C720 for $60 and swapping out the SSD for a larger one is pretty easy.  That model has a fantastic CPU - more than enough for presentations and even light virtualization.

---

