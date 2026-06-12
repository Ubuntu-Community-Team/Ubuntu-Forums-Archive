---
title: "turning on hardware virtualization on my Thinkpad caused sound to stop working"
date: 2010-01-06
forum: Hardware
---

### Post by metalf8801 on 2010-01-06
I turned on hardware virtualization in my bios on my Lenovo Thinkpad T60 and then when I booted into Ubuntu my sound didn't work anymore. The fix was simple all I had to do was 

[LIST=1]
[*]Open Sound Preferences which can be done by right clicking on the speaker icon in the Notification Area and clicking on Sound Preferences or System > Preferences > Sound
[*]Click on the Hardware tab
[*]Change Profile from Stereo (IEC958) Output + Analog Stereo Input to Analog Stereo Duplex
[/LIST]
Then my sound worked again 

but aside from wanting to help anyone who might run into the same problem I'm also wonder why did this happened? If anyone knows or has a really good guess please tell me. 

Thanks 
Dan

---

