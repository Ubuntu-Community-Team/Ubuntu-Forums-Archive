---
title: "Suspend/Resume Issue IBM x23 with ATI Radeon Mobility Card"
date: 2008-08-04
forum: Hardware
---

### Post by davidok on 2008-08-04
Hi, 
Sorry, but I am new to Ubuntu (and linux in general) but have been loving it so far.  I have been trying to figure out how to fix my suspend/resume problems - 
first the backlight doesn't turn off (well it turns off and then comes back on)
second when it resumes (or doesn't really) the screen goes black and does nothing...

I have an IBM x23 (yeah it's old...) and an ATI Radeon Video card.  
I downloaded the Radeontool package, but am not sure how to get that to work for turning off the back light.

I know that this question has been asked in the past (or at least similar variants) but i haven't been able to figure out how to get it to work for me
thanks!
david

---

### Post by tuxxy on 2008-08-04
I had similar issues running an ATI card with Hardy 64bit, I solved it by disabling any power management features from system > prefs > screensaver > power management

---

### Post by davidok on 2008-08-04
> **tuxxy said:**
> I had similar issues running an ATI card with Hardy 64bit, I solved it by disabling any power management features from system > prefs > screensaver > power management

Unfortunately, this didn't work for me.  Same problem with backlight turning off and then back on.  Then when pulled out of suspend it begins to come back - looks good, then goes dark and can't be recovered...
thanks

---

### Post by davidok on 2008-08-04
I have also tried a couple of the things listed on this thread:
[http://ubuntuforums.org/showthread.php?t=782782&highlight=suspend+resume+problem](http://ubuntuforums.org/showthread.php?t=782782&highlight=suspend+resume+problem)
but to no avail...
Including trying to setup hibernate and trying to change the /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux file.

any other suggestions?
thanks!

---

### Post by davidok on 2008-08-10
I found the solution here:
[https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/148408](https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/148408)
except that the backlight still doesn't go off.
but at least it resumes now.
any ideas with the backlight?

---

### Post by davidok on 2008-08-10
I found the solution here:
[https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/148408](https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/148408)
except that the backlight still doesn't go off.
but at least it resumes now.
any ideas with the backlight?

---

