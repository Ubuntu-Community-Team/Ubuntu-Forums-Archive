---
title: "sleep works, but only every other time"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by vmueller on 2006-11-09
New to Ubuntu, as of the release of Edgy (came from Mepis).  I'm running Edgy on a Dell Inspiron 710m.  I am pleased with the power management capabilities and compatability--I can finally make my computer SLEEP!  (Suspend to Ram)

The only problem I have is the following:

When I close the lid on my laptop, I can only get the box to sleep ever OTHER time.  In other words, it works one time and then it doesn't work the next time and then it does work the next.  I have a hunch it may have something to do with whether Ubuntu thinks the lid button is a SWITCH or a TOGGLE.  Does anyone know how to make it sleep every time on lid close?

P.S. I can get it to sleep every time if I click on the power management icon in the task bar, just not when the lid closes.

Thanks!

---

### Post by vmueller on 2006-11-14
Does anyone have any ideas?  I'm pretty new to this, so I'm not sure even how to begin figuring this out.  I've googled this pretty extensively, but can't find any similar problem.

---

### Post by su99 on 2007-04-10
hi vmueller,

i got exactly the same problem on exactly the same laptop. only difference is that i'm running 7.04 (feisty), not 6.10 (edgy). but the issue pattern is the same: lid close only works for 2nd/4th/6th/8th time, not 1st/3rd/5th/7th.

unfortunetely i don't have the definitive solution for now. but i did dig it a little bit further and believed it is related to the wrong lid state value in hal. a failed suspend will set the lid state to the correct value so the next time it works correctly; but a correct suspend/resume will leave the lid state in a wrong state so the next time it fails.

check my post here:

[http://ubuntuforums.org/showthread.php?t=406250](http://ubuntuforums.org/showthread.php?t=406250)

update: i might have a solution now. it's described in the above post. if possible please try it and let me know if it works. on the other hand, if you already got a different solution, let me know too. maybe yours will be better.

thanks.

---

