---
title: "Cintiq 12wx tablet-screen-mapping issue - Karmic"
date: 2010-02-21
forum: Hardware
---

### Post by sysiphus80 on 2010-02-21
Hello! 

I'm new to ubuntu and need help! I've got a normal monitor and a Wacom cintiq. The tablet is recognised but at the moment the cursor is not in place with the stylus or eraeser and can be moved across the whole desktop (monitor and cintiq). 

How can i restrict the stylus to the cintiq(-monitor) and achieve that it's in place with the cursor? :confused:
I already tried to play around with my "10-linuxwacom.fdi" and its parameters (top bottom x y) but without luck. 

Please help me. 

Thank you in advance for your help

Roland

---

### Post by Favux on 2010-02-21
Hi sysiphus80,

Welcome to Ubuntu forums!

It partly depends on your video card/chipset and then what kind of "video" setup you have.  This thread is a little dated but may help:  [http://ubuntuforums.org/showthread.php?t=1185904](http://ubuntuforums.org/showthread.php?t=1185904)  You may just need to specify the screen number.

Hope this helps.

---

### Post by sysiphus80 on 2010-02-23
Hello Favux!

Thank you very much for your welcome and help. Adding those view lines worked instantly! :D

I've got another little question:

Since there is still a litte spacing between stylus and cursor left  i wanted to know if there is some trick to finetune that? (i already tried it with wacomcpl and calibration but if i do that the spacing even grows)

Roland

---

### Post by Favux on 2010-02-23
Hi Roland,

Great!
> Since there is still a litte spacing between stylus and cursor left i wanted to know if there is some trick to finetune that? (i already tried it with wacomcpl and calibration but if i do that the spacing even grows)

Not quite sure what you mean.  Assuming you've got the screen dimensions correct (might try fiddling with them a little) I'm not sure.  Wacomcpl should let you calibrate.  Do you have it set up so that its settings persist across a reboot?

That said the LWP project always seems to be adding patches to "fix" TwinView.  I gather you are in Karmic and have the default linuxwacom 0.8.4-1?

---

