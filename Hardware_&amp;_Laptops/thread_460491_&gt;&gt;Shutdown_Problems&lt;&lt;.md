---
title: "&gt;&gt;***Shutdown Problems***&lt;&lt;"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by Eaglejazz on 2007-05-31
I was just wondering if someone can offer some advice for my problem.

Specs: Dual boot Toshiba Laptop - (Fiesty/WinXp)
              Bootloader is GRUB.

**Problem:** 

When exiting Ubuntu it hangs up and i have to manually shut it down by pressing the power button. So i if i try to power it up again soon right after it either gives me black screen or it gives me resized screen before BIOS screen : example HP -> HP welcome sign, or Intel Screen and does not go any further, hangs up on me. So i have to usually wait for 20 minutes to an hour. However when exiting windows this error does not occur. Restarting doesnt work with ubuntu either properly. 

If anyone can tell me the solution to getting rid of this problem it would be a great help, i will be willing to give you more info if you wanted as well if this is too vague description for you! 

Cheers :)

---

### Post by eggdeng on 2007-05-31
Try adding
```
apm power_off=1
```
to the /etc/modules file or have a look at this thread [http://ubuntuforums.org/showthread.php?t=290713](http://ubuntuforums.org/showthread.php?t=290713)

---

