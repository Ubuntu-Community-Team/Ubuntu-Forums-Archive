---
title: "Tecra A3 resolution doesn't last beyond login"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by barak on 2006-09-22
I am having trouble, as everyone seems to, with the screen resolution on my laptop.  I have a Toshiba Tecra A3 - which in WindowsXP supports 1152x864 on both the internal panel and using my external crt screen.

I have got dual screen setup, finally.  Turning off dri helped a lot.

Linux seems to default to 1024x768 for both the lcd and crt.  The logs in /var/log/Xorg say that the lcd panel is only 1024x768?  How can this be if windows displays higher?

For the crt I have been trying to use 915resolution to convert one of the unused bios settings to 1152x864@75 that the screen says it can do in the modeline setting (SyncMaster 750Ms).  It can do 1280x1024 and 1600x1200 but both are at 60-Hz (ouch my eyes!).  1152x864 seems to work for the login screen, then the whole screen resolution changes as it is setting up the window manager - back to 1024x768 and the option that i used in 915resolution 1600x1200 has disappears from settings->display.
The logs say that there is no setting 1152x864@75 - yet ForceBIOS is set, modes "1152x864@75" set, modeline "1152x864@75" is set...
And in the log I can see that Mode: 3a (1152x864) - whereas all my other attempts would make it look like Mode: 5a (0x0)...
If I use 915resolution on more than 1 bios setting then the all go as above (0x0), so if I try and change 1024x768 to 1152x864 then the option will disappear from settings->display and the resolution will decrease...

Is there something I could be missing in setting this up or will I just never be able to go over 1024x768. Are there other drivers I need?

---

