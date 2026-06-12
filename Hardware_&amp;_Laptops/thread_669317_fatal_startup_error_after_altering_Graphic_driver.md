---
title: "fatal startup error after altering Graphic driver"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by Lektorvis on 2008-01-16
In my efforts to get Compiz running on my Dell Latitude D830 I tried to choose a different driver (I830 sometning...) under the "Screen Option" menu. 
After the reboot Ubuntu failed to complete the load-procedure:

I see the Ubuntu load screen
then some lines like this:
* Staring anac(h)ronistic cron anacron    [OK]
* Starting deferred execution scheduler atd [OK]
* Starting periodic command scheduler crond [OK]
* Enabling additional executable binary formats binfmt-support [OK] 
* Checking battery state [OK]
* Running local boot scripts (/etc/rc-local) [OK]
-
Then I only see the cursor blinking - nothing more happens.

I'm not familiar with Linux codes, is it possible in a simpel manner to recover the system? 
Or else, can do a new install over the old linux partion?

Thanks for your help

---

### Post by renzokuken on 2008-01-16
reisntall shouldnt be needed.

simply hit Ctrl+Alt+F1 to get to a command line screen and run

```
sudo dpkg-reconfigure xserver-xorg
```

follow the wizard through and when you get to the driver screen simply select another driver depending on what grafix card/chipset you have.

driver "vesa" is a good failsafe one that works on most hardware if you're unsure

---

### Post by Lektorvis on 2008-01-16
Thanks Renzokuken 
All though the code didn't work for me at first; it inspired me to solve the problem in an other way. I used the gedit command from the Terminal in the Live CD and renamed the     xorg.conf.1 to xorg.conf.
Works OK now :)

---

