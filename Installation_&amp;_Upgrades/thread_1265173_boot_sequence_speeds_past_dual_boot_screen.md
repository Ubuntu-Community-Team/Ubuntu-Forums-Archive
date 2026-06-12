---
title: "boot sequence speeds past dual boot screen"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by pdc on 2009-09-13
I installed an Ubuntu variant (easy peasy) on a Eee 1000H; 

the Eee originally had XP on it; I shrank the Windows partition, and installed ep; this crashed recently;

MY PROBLEM: since then, the boot sequence flashes immediately past the dual boot option, and boots only Easy Peasy; EP runs well;

REQUEST: can anyone guide me to what files might need to be edited, to allow the dual boot screen to remain evident for enough time for someone to choose XP, or any other linux distros I may select;

(I thought to attempt to repair, before adding another distro)

many thanks for any guidance that can be offered

---

### Post by mcduck on 2009-09-13
> **pdc said:**
> I installed an Ubuntu variant (easy peasy) on a Eee 1000H; 

the Eee originally had XP on it; I shrank the Windows partition, and installed ep; this crashed recently;

MY PROBLEM: since then, the boot sequence flashes immediately past the dual boot option, and boots only Easy Peasy; EP runs well;

REQUEST: can anyone guide me to what files might need to be edited, to allow the dual boot screen to remain evident for enough time for someone to choose XP, or any other linux distros I may select;

(I thought to attempt to repair, before adding another distro)

many thanks for any guidance that can be offered

do you mean you have less than the 3 second minimum time to access Grub menu? In that case Grub must be broken, as none of it's options allows shorter time than the 3 second minimum..

Note that you only need to press any button during that time (if the menu is visible) or Esc (if the menu is hidden) to stop the time from counting.

Anyway, the time is set in /boot/grub/menu.lst

---

### Post by pdc on 2009-09-13
thanks for a very prompt reply; it is very kind of you and much appreciated;

I see in our linux mint desktop that the line

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

has time out of 5 and in Easy Peasy, I see it is zero;

........ so if I just add 5, to replace the zero ?

I tried holding the esc key down during boot, but it still tripped over the option; (perhaps I should have repeatedly taped the esc key)

---

### Post by pdc on 2009-09-13
great;

just added 7 seconds (because I can be slow);

and all is well;

thanks mcduck; your prompt and knowledgable help much appreciated; 

keep warm in Finland; best wishes

---

### Post by mcduck on 2009-09-13
> **pdc said:**
> great;

just added 7 seconds (because I can be slow);

and all is well;

thanks mcduck; your prompt and knowledgable help much appreciated; 

keep warm in Finland; best wishes

No problem, great that you got the problem solved.

(and luckily it's still quite warm in here.. At least for a while until the winter comes.. :D)

---

### Post by newsoft on 2009-09-13
> No problem, great that you got the problem solved.

(and luckily it's still quite warm in here.. At least for a while until the winter comes.. )

Still VERY HOT here though :)

---

