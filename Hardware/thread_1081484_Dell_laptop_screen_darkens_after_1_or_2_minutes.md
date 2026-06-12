---
title: "Dell laptop screen darkens after 1 or 2 minutes"
date: 2009-02-26
forum: Hardware
---

### Post by TimDaniels on 2009-02-26
After one or two minutes of inactivity - like when I'm reading a news article - the screen on my Dell XPS M1330 laptop darkens if it's on battery power. It doesn't do this under converter power or under Vista. It seems to be an Ubuntu battery management thing. Is there a parameter that will extend the timeout period for full screen brightness, and if so, how does one access it?  This short timeout only started after I re-installed Hardy 8.04

*TimDaniels*

---

### Post by TimDaniels on 2009-02-26
A poster in the Dell forum pointed me at System/Preferences/Power Mangement/On Battery Power tab, and 2 check boxes there took care of dimming when on battery: 
Reduce Backlight Brightness, and Dim Display When Idle.

*TimDaniels*

---

### Post by mtbsoft on 2009-02-26
It's a power saving feature.  Go to... 

*System* | *Preferences* | *Power Management* | *On Battery Power* tab

To disable the dimming, un-check the *Dim display when idle*

If you want to keep but change the amount of time before it dims, use...

*Applications* | *System Tools* | *Configuration Editor* | *Edit* | *Find* 

...and search for *idle_dim_time*.  It is initially set to 30 (seconds) - adjust it to whatever interval suits you.

---

### Post by TimDaniels on 2009-02-27
> **mtbsoft said:**
> 
If you want to keep but change the amount of time before it dims, use...

*Applications* | *System Tools* | *Configuration Editor* | *Edit* | *Find* 

...and search for *idle_dim_time*.  It is initially set to 30 (seconds) - adjust it to whatever interval suits you.

Thanks, that's better for me than leaving it bright indefinitely.

*TimDaniels*

---

