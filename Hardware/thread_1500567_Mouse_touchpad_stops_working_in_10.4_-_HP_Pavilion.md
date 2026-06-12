---
title: "Mouse touchpad stops working in 10.4 - HP Pavilion dv6000"
date: 2010-06-03
forum: Hardware
---

### Post by AnBéalBocht on 2010-06-03
Hi all, recently upgraded to 10.4 LTS without problem from 9.10. On my laptop there's a mouse touchpad (if that's what it's called...) and it has a button that can switch it on and off. I switched it off and back on last night and it froze the menu bar and the arrow no longer moves whether switched on or off in my user profile. At the log in screen and the other user profile, the touchpad works fine, but it just doesn't work anymore on this profile and i'm not sure how to fix it.

I tried switching it off and on a while ago but it froze the menu bar again and i had to hold the power button to turn off the computer forcibly again.

any ideas on how to sort this out will be much appreciated! :)

---

### Post by AnBéalBocht on 2010-06-03
bump

---

### Post by AnBéalBocht on 2010-06-04
Does anyone have an idea? The settings for the mouse are the same as in the other profile, it's just after I've logged into this profile that it doesn't work. Any ideas will be much welcomed.

---

### Post by KingJeremy on 2010-06-05
Having the same problem on a tx2110us.  Been Googling for info for an hour now.

---

### Post by EricN on 2010-06-05
Have been having a very similar problem with the touchpad on my HP Pavilion.  I finally got it fixed as per the advice on this thread.

[http://ubuntuforums.org/showthread.php?p=9410163]("http://ubuntuforums.org/showthread.php?p=9410163")

It's not a full fix as turning my touchpad on and off still causes the touchpad to quit working (and also causes my keyboard to become non-responsive).  However, once I made this config file, then restarting my computer fixes the problem.  Not a complete fix, but its a hack for now.  

Has someone reported this bug?

---

### Post by ibbqalot on 2010-06-16
Well, im having the same problem here .. when i reboot it's all fine .. anyway what i do is i press alt + f1 and go to keyboard and enable using mouse through keyboard and i use my numpad as a mouse .. but if you had a smaller laptop you wouldnt have a num pad :S
:popcorn::popcorn::popcorn:

---

### Post by ibbqalot on 2010-06-16
ya and there's some program called mousetweaks .. download it, pretty usefull

use ==> sudo apt-get install mousetweaks

hope it helps

:popcorn::popcorn::popcorn:

---

### Post by xtek0 on 2010-08-12
> **EricN said:**
> Have been having a very similar problem with the touchpad on my HP Pavilion.  I finally got it fixed as per the advice on this thread.

[http://ubuntuforums.org/showthread.php?p=9410163]("http://ubuntuforums.org/showthread.php?p=9410163")

It's not a full fix as turning my touchpad on and off still causes the touchpad to quit working (and also causes my keyboard to become non-responsive).  However, once I made this config file, then restarting my computer fixes the problem.  Not a complete fix, but its a hack for now.  

Has someone reported this bug?

I can vouch for this fix, simple and easy. I first thought it was the ram failing. Instead i popped this line of code in and it worked like a charm.

Good job team.

---

### Post by mgysgthath on 2010-10-19
I can confirm the same problem on an HP dv6426ca laptop.  The keyboard stops working and the mouse won't entirely click on anything, after enabling or disabling the touchpad with the toggle.

This is on Ubuntu 10.4 LTS - Clean install - not upgraded.  If I use a USB mouse and don't touch the touchpad toggle, it will remain working.

---

