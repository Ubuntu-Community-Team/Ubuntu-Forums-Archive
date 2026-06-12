---
title: "[SOLVED] Drivers for video cards"
date: 2008-10-11
forum: General Help
---

### Post by DougieFresh4U on 2008-10-11
I am not sure what is going on but I will explain  the best I can.
On start up of machine, after Login and Password, I get a little pop-up telling me 'Ubuntu is running in low graphics mode' (what does that mean?) Then another box pops up asking to fix or run it in low graphics mode. I have chosen the try to fix. While doing the fix it is choosing the vesa driver and every time I change it to intel865 it changes it back to vesa, Why would this be happening? Also CPU is running at 99% or 100% with nothing going on and while using Swiftweasel (my choice of browser) scrolling up and down page is very jumpy and I have it set to 'Smooth Scrolling'(E-mail scrolls smooth)
How do I get machine to use the intel865 graphics?
I am just confused by all this and how do I stop this low graphics mode?
Sorry for the ramble on :)

---

### Post by chriskin on 2008-10-11
i had the same problem last week

the system/administration/hardware drivers menu had two options for me, so i chose a different driver and the problem stopped

i don't know if this helps, but it seems to be the same problem

as for the others, i have no idea




also, i see that you are using intrepid ibex
after i made the last partial upgrade available, i could use any drivers i wanted for the video card, try upgrading again

---

### Post by Yellow Pasque on 2008-10-11
Doug, you want to use the generic "intel" driver, not the "i815" driver.

---

### Post by DougieFresh4U on 2008-10-11
> **Temüjin said:**
> Doug, you want to use the generic "intel" driver, not the "i815" driver.

Thanks.
Every time I change the driver it seems to always go back to vesa on it's own.
Also 'generic' for intel list 740(generic). Is that the one you mean? But like I said, when I go back to check it's listed the vesa aagain.
Can you provide code to give me output of what it's currently using. Is it 'grep' something?Also when I change driver and click the test button terminal says all errors

---

