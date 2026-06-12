---
title: "Screensaver goes black and won't return to life"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by indiadawwg on 2007-09-21
I have a Toshiba Satellite A10 running ubuntu as my operating system.  It works perfectly, except now sometimes the screen doesn't come back up after it turns black after remaining idle for awhile (it's set up to do that after 30 minutes).  In the end, I have to switch off and on again to get back to work.

Can anybody help?

---

### Post by caedmon on 2007-09-21
Hi, I'm not really an expert either, but have experienced similar symptoms. *Standby* is not always supported on laptops, so you may want to look into this. Also, ctrl alt backspace should return you to your log in as switching on and off is not good!

hope that helps untill you get better advice......


:lolflag:

---

### Post by banewman on 2007-09-21
I had a similar problem that was the result of a setting in my bios that turned things off after fifteen minutes. Looking at your bios settings might help. :)

---

### Post by SeanBlader on 2007-09-21
I had a similar issue with my Inspiron 8500. What fixed it was not using ACPI to blank out the screen but just using the screensaver black. Also if you see the black screen like it's still there and the backlight is still on, try typing in your password very carefully and hitting enter. You may find that it's just the screen is black and the login window isn't popping up. That could be an interesting security trick.

In the end I had to follow the bottom steps on this help file and now my nvidia will start back up after it goes into suspend.
> [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

I think it was because of this step:
> we need to force the nvidia module to load early, this is done because it hooks in with the agpgart module and needs to load before that module does, so simply add 'nvidia' to the top of /etc/modules

After that and one initial test the nvidia will now startup from suspend.

---

