---
title: "Jaunty and ATI woes"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Kepesk on 2009-04-27
Yes, I was one of the poor saps with one of the X-series ATI cards (specifically X1650) who were tumbled into limbo after upgrading to Jaunty.  You'd think some kind of warning would have been a good idea?  By the looks of the forums, there are a ton of people who are in the same situation.

However, what makes my situation a particular nuisance is that I was using the ATI drivers because the open-source drivers don't work for me.  Now I'm left with a computer that won't display any useful video.

Long story short, I was able to ssh in to my system from another computer and successfully remove the ATI drivers and install the open-source drivers.  However, the open-source drivers have decided that the only resolution that can be displayed is something ridiculous like 2236x480.

So naturally, I tried going into xorg.conf to add proper resolutions only to discover that that has changed as well.  The xorg.conf has been completely gutted, and apparently the information now comes from somewhere else.  I tried to add modeline entries anyway, but I clearly don't understand the new system, because anything I add causes errors on startup, anything from type1 not found to no valid modes found.

I have no clue where to go from here.  Because I don't understand the new xorg system, I'm not even sure what logs to look through.  To summarize:

1. ATI drivers no longer support my Radeon X1650 video card.
2. Open-source drivers try to use a ridiculous resolution in the vicinity of 2236x480
3. Adding resolutions to xorg.conf causes various errors during boot, and reverts the machine to low-graphics mode.
4. Vesa drivers are useless to me because it doesn't display text properly in one of the programs I use (MythTV)

I never expected to be gored by the jackalope...

---

### Post by flipfone on 2009-04-27
Kubuntu - 64 bit machine - Radeon x1650 after the upgrade all i get are lines at the top of the screen ive reset xorg.conf back to defaults tried copying an older one in, tried making the changes from the bug list, i tried both changing the AccelMethod to UXA and i tried changing the driver to "vesa" any ideas?

ok ive downloaded the live dvd and it boots up just fine, the video isnt right then a moment later it straightens out and all is well. after i saw that i listed out xorg.conf and used the command listed there to reset the video. this didnt seem to work. any ideas folks?

these were my 2 posts 2 weeks ago. and noone wants to help me either.

---

### Post by phantom3113 on 2009-04-27
I have an ATI Radeon, but I didn't see any problems on the live cd video-wise. Would the live cd be different than the install?

---

### Post by Kepesk on 2009-04-27
The problem only affects people who were using the ATI drivers with the following cards: [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

Still, that's a lot of people.  Can anyone point me in the right direction?

Thanks in advance!

---

### Post by Mark Phelps on 2009-04-27
I upgraded from 8.10 to 9.04 and am using the open source drivers because my x1600 was one of the cards that ATI "abandoned" in the latest Catalyst 9.4 drivers.

I've hear rumours that ATI is rethinking their abandonment stance -- but only time will tell whether or not that is anything other than wishful thinking.

I don't think it's really a matter of no one wanting to help ... I just think that there aren't any good options.

You could check the Phoronix forums using the link below to see what they are doing:

[http://www.phoronix.com/forums/forumdisplay.php?f=19]("http://www.phoronix.com/forums/forumdisplay.php?f=19")

---

### Post by Kepesk on 2009-04-27
I would be fine going to the open-source drivers; I don't need any fancy 3D acceleration or anything on this machine.  They just won't give me a useful resolution.

---

### Post by Mortus Pryde on 2009-04-27
They certainly left midrange ATI users in the lerch. I had to revert back to Intrpid so I could use the 9.3 Catalyst to get reasonble 3D exceleration for my needs. May not entirely be lack of support in the Mesa driver, as I think there is a performance bug as well, none the less not even the 9.3 Catalyst is up to par with its XP equivilent, but at least its "Good Enough".

---

### Post by zampes on 2009-04-27
I'm currently struggling with my ATi as well... ATi HD 3200 on an HPDV4 Turion X2, 4 gigs of RAM. 9.04 makes my screen flicker like hell. No 3D acceleration whatsoever, Ubuntu doesn't even recognize the card, it can't tell what card it is. The only way to stop the flickering is to lower the resolution from 1280x800 to 1280x768 (not vomiting material, but not good either, considering I've had my lap for 2 days now, shining new!) Second thing is, I'd rather have bad resolution to Windows Vista, anytime.
Help, anyone?

---

### Post by Kepesk on 2009-04-28
You definitely don't have the same problem as I do; your card wasn't one of the ones for which support was dropped in the proprietary drivers.  However, you do seem to be stuck in a similar limbo as me concerning the drivers.

---

