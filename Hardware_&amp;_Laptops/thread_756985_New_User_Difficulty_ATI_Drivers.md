---
title: "New User Difficulty ATI Drivers"
date: 2008-04-16
forum: Hardware &amp; Laptops
---

### Post by nathanael on 2008-04-16
I am a new user to linux.  I migrated from xp pro by installing wubi, I am working with Ubuntu 8.04, I have no 3D acceleration with my Radeon Mobility 7500C.  I am an avid user of Blender 3d, and it runs a bit slowly, and I cannot enable desktop effects. I have seen other forum posts concerning this issue, but I do not understand what they are talking about.  For example, many people say to try the DIR drivers.  I am clueless about installing those.  Thank you very much for your help.

---

### Post by VeN0mizer on 2008-04-16
Have you tried enabling the restricted drivers that come with Ubuntu? Click System->Administration->Hardware Drivers, and you *should* see your card manufacturer (ATI) listed there...Check the "Enabled" box, or if it is already checked, uncheck it, click apply, then reboot...then come back and check it again, click ok, then reboot and see if that helps....After you have ensured they are enabled AND HAVE REBOOTED (it will instruct you to do so), type in "glxinfo | grep direct" (without the quotes) at the terminal Applications->Accessories->Terminal and see if "Direct rendering enabled" says YES to see if the drivers are working properly...let us know how it goes and good luck! :)

P.S. I haven't gotten Envy to work right for me on Hardy yet with my ATI card, but you might give it a shot if the above solution does not work for you.

ATI is a pain in the royal rear end when it comes to their drivers not working right in linux ( and sometimes windows :( ) But once you get them installed, set it and forget it lol

---

### Post by nathanael on 2008-04-16
Thank you very much for the quick response.

I checked restricted drivers, and it was not available.  The mobility 7500c is an oem driver, and is not available anywhere online, except from dell, or whoever manufactured the laptop with that card.  I ran the terminal and direct rendering says "no"

Where do I go from here?

---

### Post by ile on 2008-04-16
Take a look:

[http://ubuntuforums.org/showthread.php?t=754440&highlight=ati](http://ubuntuforums.org/showthread.php?t=754440&highlight=ati)

Thats not exactly your problem, but in some post you can read:

"The fglrx driver does not support such an old card (anything older than radeon 9500 was abandoned by ati almost two years ago).
You should be able to get the open source "radeon" driver working (by setting the driver to either "radeon" or "ati" in xorg.conf).
I doubt you will ever be able to use the tuner of that card.
Make sure you start with a fresh xorg.conf by using:
Code:

sudo dpkg-reconfigure xserver-xorg"

May that be your problem?

---

### Post by VeN0mizer on 2008-04-16
I wish I could de-solder my X1300 ATI from my laptop...I'm getting sick of poor AIGLX support and their fixing only like one bug a month....pathetic....I used to hate nvidia (and who would blame me? I had THREE IN A ROW die on me when building a lady's computer and the fourth one finally worked out for me)...but after seeing how half assed ATI's drivers are, I'm getting downright angry with them and wish I had an nvidia card for the great linux support...

---

### Post by nathanael on 2008-04-16
I tried that, and it could not understand the command "reconfigure."  I finally got desktop effects to work by uninstalling the default drivers and installing alternative ones, but the computer slowed down.  I disabled them, and it had extreme difficulty drawing windows.  I don't know what to do anymore, since I had it under wubi, I just uninstalled it, I will wait 8 days for the official release of Hardy Heron.  Thank you for your help everyone.

---

### Post by ile on 2008-04-18
> **VeN0mizer said:**
> I wish I could de-solder my X1300 ATI from my laptop...I'm getting sick of poor AIGLX support and their fixing only like one bug a month....pathetic....I used to hate nvidia (and who would blame me? I had THREE IN A ROW die on me when building a lady's computer and the fourth one finally worked out for me)...but after seeing how half assed ATI's drivers are, I'm getting downright angry with them and wish I had an nvidia card for the great linux support...


Sure, man. Same here.

---

### Post by ile on 2008-04-18
> **nathanael said:**
> I tried that, and it could not understand the command "reconfigure."  I finally got desktop effects to work by uninstalling the default drivers and installing alternative ones, but the computer slowed down.  I disabled them, and it had extreme difficulty drawing windows.  I don't know what to do anymore, since I had it under wubi, I just uninstalled it, I will wait 8 days for the official release of Hardy Heron.  Thank you for your help everyone.

Thats what i would do. GL.

---

