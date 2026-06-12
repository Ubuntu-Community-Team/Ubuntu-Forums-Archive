---
title: "Intel X3100 + Maximum Resolution"
date: 2008-08-08
forum: Hardware
---

### Post by rakeshxp on 2008-08-08
I have Acer Aspire 5920 with Intel Mobile GMA X3100 graphics card. The maximum resolution that I can see using System -> Preferences -> Screen Resolution is only 1280 X 800 ( @ 60 Hz ). 

Is it possible to increase the resolution to 1280 * 1024 OR 1280 * 1280 ?

Thanks in advance!

---

### Post by syczu on 2008-08-08
You can try edit your xorg.conf file

sudo gedit /etc/X11/xorg.conf

scroll down to 'Modes' section and type your 'resolution@refresh rate'. Now you should have in system->preferences->screen resolution new resolution to choose.

---

### Post by evets25 on 2008-08-08
> **rakeshxp said:**
> I have Acer Aspire 5920 with Intel Mobile GMA X3100 graphics card. The maximum resolution that I can see using System -> Preferences -> Screen Resolution is only 1280 X 800 ( @ 60 Hz ). 

Is it possible to increase the resolution to 1280 * 1024 OR 1280 * 1280 ?

Thanks in advance!

You don't want to set your resolution to either 1280*1024 or 1280*1280. If your resolution is set to 1280*800 by default, then that probably means you have a widescreen display, since that's a widescreen resolution. 1280*1024 is a resolution for normal non-widescreen displays, and 1280*1280 is a resolution for nothing. Either of those would make everything on your screen looked warped. Now, it might be possible to go to the next higher widescreen res, but you probably don't want to, since from what I discovered after a quick google search, 1280*800 is the native resolution for that screen. Anything else would either look huge and grainy, or too small to read.

---

### Post by rakeshxp on 2008-08-08
> **evets25 said:**
> You don't want to set your resolution to either 1280*1024 or 1280*1280. If your resolution is set to 1280*800 by default, then that probably means you have a widescreen display, since that's a widescreen resolution. 1280*1024 is a resolution for normal non-widescreen displays, and 1280*1280 is a resolution for nothing. Either of those would make everything on your screen looked warped. Now, it might be possible to go to the next higher widescreen res, but you probably don't want to, since from what I discovered after a quick google search, 1280*800 is the native resolution for that screen. Anything else would either look huge and grainy, or too small to read.

Thanks for the input! Guess, I have to stick with the current resolution. So what DPI should I be using with 1280 * 800 and how to set it up ? ( When I see the current installation, somehow I feel that things like icons etc are occupying lot more space than a similar resolution in winxp. )

---

### Post by phidia on 2008-08-08
You can change font size from System > Apperances and make other changes from there too. If your upper or lower panels are too big you can right click on them and choose properties to adjust the size. 
BTW from [this]("http://techreport.com/forums/viewtopic.php?f=29&p=814781") gamer site and other remembered discussions on this it's not actually possible to go higher than the resolution the screen was made/designed for-you can try but I don't believe you can.

You may want to look at the Customizing and Maintaining Ubuntu Section [here]("https://help.ubuntu.com/community/").

---

### Post by phidia on 2008-08-08
Sorry double posted-I only clicked once :(
You can change font size from System > Apperances and make other changes from there too. If your upper or lower panels are too big you can right click on them and choose properties to adjust the size. 
BTW from [this]("http://techreport.com/forums/viewtopic.php?f=29&p=814781") gamer site and other remembered discussions on this it's not actually possible to go higher than the resolution the screen was made/designed for-you can try but I don't believe you can.

You may want to look at the Customizing and Maintaining Ubuntu Section [here]("https://help.ubuntu.com/community/").

---

### Post by stchman on 2008-08-08
> **rakeshxp said:**
> I have Acer Aspire 5920 with Intel Mobile GMA X3100 graphics card. The maximum resolution that I can see using System -> Preferences -> Screen Resolution is only 1280 X 800 ( @ 60 Hz ). 

Is it possible to increase the resolution to 1280 * 1024 OR 1280 * 1280 ?

Thanks in advance!

That laptop LCD has a native resolution of 1280x800.  It will not support anything over that resolution.

---

