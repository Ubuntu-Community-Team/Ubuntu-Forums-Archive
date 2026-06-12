---
title: "Ubuntu installation problem... am I missing something"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by pzell929 on 2009-02-17
I've been trying for three weeks to get Ubuntu (or Kubuntu) running on any of my three computers - with no success. I have a laptop and two desktops and have tried to get ubuntu installed on all three of them at different times and been met with different errors every time. 
My first desktop is a brand new build, Intel Core2 Duo, 4gb of RAM, 512 MB Nvidia graphics card. I downloaded the Ubuntu 8.10 iso, checked the md5sum, and went to install. No luck, Ubuntu says there's no hard drive found. Funny thing is, Windows XP installs without a hitch. I've tried all kinds of configurations (SATA drive, IDE drive, RAID, different BIOS settings) with no luck. I can't get past the "no hard drive found." I combed the forums and racked my brain for 2 weeks... nothing. It won't install. I tried Kubuntu 8.10 and had the same result. The machine runs XP like a champ though.
My second desktop is a 3 year old dell, when I couldn't get the new computer to work, I decided to try on my old faithful. This time it installs, but I can't get any kind of GUI. When I try to boot into the desktop there's something weird with the video card drivers, the monitor blinks on and off about 7 times (seriously) then I get about 3 inches of horizontal red lines across the middle of the screen, and a 3x3 inch square of vertical lines in the upper left hand of the screen. That's where it stops. Once again, I've tried different configurations (different graphics cards, different monitors, different BIOS settings) and combed the forums; but to no avail, I still have no Ubuntu.
Finally I decided to try installing it on my laptop - just to see what would happen. -here's the kicker- Ubuntu installs beautifully, loads right up, and when I get to the main login page, the entire desktop shifts about 2 inches to the right and starts scrolling down rapidly. (remember watching broadcast TV when the signal was bad? the screen starts wrapping down incessantly? this looks the same way.) That's the only way I can think to describe it. As the screen tumbles I can manage to login and get past the initial screen, but the scrolling never stops. 
So there you have it. All three systems with completely different problems. I read on these forums and it looks so easy to get ubuntu installed and running. But I must just be missing something. I've downloaded the Ubuntu and Kubuntu iso's several times each, tried to install each of them several times, and I get absolutely nothing. 
To be having problems like this on three computers... please tell me I'm missing something basic...

---

### Post by Jadifabbio on 2009-02-17
Did you try to test the CD for errors?
Did all of the menu options on the live cd come up on each computer you tried to install on?

---

### Post by pzell929 on 2009-02-17
yes, and yes. I downloaded the iso's several times, checked them, and burned them onto several different discs - I even tried it from a USB drive a couple of times just for kicks. 

One thing I forgot to mention, the Live CD comes up and runs on the first computer (the new build), but I get the same problems on the other two whether I use the live CD or install it.

---

### Post by Jadifabbio on 2009-02-17
I have had that graphics problem before when using my 1440x900 HP display and i think it just needs to be fully updated before the drivers will actually support that resolution.  It looked
just like how you said, shifted to the right 2".  

So after you boot and try to install it, you cannot find a partition in the editor to allocate for the intall?

---

### Post by pzell929 on 2009-02-17
I tried it on a two different CRTs, an LCD, and a DLP projector. All with the same result. 
When I boot with the live cd no hdds show up at all, even though they are recognized in the BIOS.

---

### Post by Jadifabbio on 2009-02-17
I had the same problem with the partition editor so i put in my western digital boot cd and partitioned my drive into 3 parts all around 100 GB each and then the editor saw them the next time it booted to install.

---

### Post by pzell929 on 2009-02-17
I created partitions on my drive less than 100 gigs with no luck. I also tried using an 80 gig IDE drive and no results

---

### Post by Jadifabbio on 2009-02-17
I will try to figure out anything else i might have done to get it to work and get back to you.  Leavin work now so ill to that in a little bit.

---

