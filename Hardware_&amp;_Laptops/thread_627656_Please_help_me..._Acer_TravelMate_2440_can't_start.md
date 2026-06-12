---
title: "Please help me... Acer TravelMate 2440 can't start"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by IF-Rit on 2007-11-30
i just use envy to install my ATI graphic card...
installation going smoothly..
and then restart requiread..
after i restart my laptop can't startup...
the screen blank for a long time and can't show a login page.

Please i need help..

---

### Post by crouton on 2007-11-30
When you get the GRUB screen, hit 'e' to edit and look for a line that has 'kernel='.  At the end of that line should be a few options like 'quiet' and 'splash'.  Remove both of those, hit Enter, and 'b' to boot using those changes (only for this boot though.)  Your system will boot up and display a lot of information, but at least you'll have a better idea what may have gone wrong.

[edit] Off the cuff it sounds like X didn't like your ATi driver.  Do you know what driver you were using before? (ati, radeon, etc)

---

### Post by IF-Rit on 2007-11-30
thanks for your attention...
i think my driver is ATI Raden Xpress 200M

---

