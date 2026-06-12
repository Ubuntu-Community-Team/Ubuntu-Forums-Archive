---
title: "nvidia FX5200 sync. freq."
date: 2009-05-16
forum: Hardware
---

### Post by Ber P on 2009-05-16
I have an old screen, which can only run 1024x768 in 50 Hz, but I'm unable to get the nvidia driver lower than 60Hz (which makes the screen flicker). I've tried adding modelines to my xorg.conf, but it seems to ignore it.
So now my question is, does the restricted nvidia driver overrule xorg.conf? And how do I get more modes with the nvidia driver?

---

### Post by Mister LinOx on 2009-05-16
I have one of the Nvidia GeForce 5 FX series as well, 5700 to be exact, and I could be wrong, but isn't the higher the screen refresh rate LESS flicker?

---

### Post by Ber P on 2009-05-17
I thought so too, but I can choose between 60, 70 and 75Hz. And the higher freequency the more flicker. 
When I run 800x600, I can choose 50 Hz, and then the screen is smooth and without flicker.
I'm not fully aware how these things are related, but my screen has an "info" menu, where it reports the actual refreshrate, resolution and other stuff. Funny enough, it's not reporting the same numbers as I choose in the nvidia control center?!?

I thought about upgrading my nvidia driver to the latest one (180), but apparently it dosen't support the 5-series. Has anyone tried if they can be used anyway?

Right after rebooting, chagning the settings in nvidia control center does nothing. After being on for about 30 min's, it starts to make a difference, and the screen gets better. Defect hardware??

---

### Post by Mister LinOx on 2009-05-17
> **Ber P said:**
> I thought so too, but I can choose between 60, 70 and 75Hz. And the higher freequency the more flicker. 
When I run 800x600, I can choose 50 Hz, and then the screen is smooth and without flicker.
I'm not fully aware how these things are related, but my screen has an "info" menu, where it reports the actual refreshrate, resolution and other stuff. Funny enough, it's not reporting the same numbers as I choose in the nvidia control center?!?

I thought about upgrading my nvidia driver to the latest one (180), but apparently it dosen't support the 5-series. Has anyone tried if they can be used anyway?

Right after rebooting, chagning the settings in nvidia control center does nothing. After being on for about 30 min's, it starts to make a difference, and the screen gets better. Defect hardware??

That is very odd as I, too, am using a 1024 x 768 pretty old Dell monitor and at 70 hertz, I am just fine.

---

### Post by Ber P on 2009-05-17
Turned out to be my monitor. Switched it with another pc - which has now screen flicker :)

---

