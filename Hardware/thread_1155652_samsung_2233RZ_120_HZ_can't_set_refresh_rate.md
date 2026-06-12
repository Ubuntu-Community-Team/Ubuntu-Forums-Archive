---
title: "samsung 2233RZ 120 HZ can't set refresh rate"
date: 2009-05-11
forum: Hardware
---

### Post by cnicog on 2009-05-11
Ok, I installed today ubuntu 9.04 x86, installed the nvidia latest drivers and I set my resolution on the nvidia X settings to 1680 x 1050 and the refresh rate to 120 Hz.. but it won't use 120 Hz and sets itself to 60 Hz..

The settings say 120 hz but the monitor info and the screen look like 60 hz... and also on Nvidia X server settings under GPU 0 and DFP 0 it shows 59.88 Hz

I've been brwsing forums and looking for an answer on google for hours now.. I found a lot of options but I tried most of em and they wouldn't work..

Does it have to do that ubuntu doesn't recognize my monitor since its practically a very recent one?

Or how can I get it to actually use the 120 Hz my LCD monitor is capable of?

thanks!

---

### Post by cnicog on 2009-05-11
Ok I fixed this already... I only had to uncheck the option "FORCE full GPU scaling", and it worked, I can now use 120 Hz.

---

### Post by garg on 2009-12-17
Hello,

sorry for bumping this.

How did you initially set the refresh rate to 120 Hz? My drop down menu only shows 60hz in nvidia-settings. 

Did you manually change it to 120 from xorg.conf?

---

