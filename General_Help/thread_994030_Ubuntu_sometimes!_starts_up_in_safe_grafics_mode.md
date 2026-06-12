---
title: "Ubuntu sometimes! starts up in safe grafics mode"
date: 2008-11-26
forum: General Help
---

### Post by christoph88 on 2008-11-26
hi

After a recent reinstall of ubuntu, it sometimes starts up in safe graphics mode. I have the most recent driver of my graphics card and it worked perfectly before. Now it still does only when I restart every now and then it starts in safe graphics mode. After a reboot the problems disappears.

I think it maybe has to do with my home directory being on a other hard disk but I'm not sure.

Can somebody please help me with this or is it a bug?

Thanks in advance

---

### Post by christoph88 on 2008-11-29
UPDATE: It only seems to happen the first time I start the computer in the morning. If I just reboot after that without selecting anything everything works fine for the rest of the day. 

Could it be that my home directory on the separate partition is loaded to late or something like that? Or does that have nothing to do it?

UPDATE 2: I think it could be my graphics card. I remember when using vista that vista sometimes hung when starting up. Same strange behaviour. Ubuntu doesn't hang but boots into low graphics mode. I'm going to see if I still have warranty and ask for a replacement.

Could this be a solution or does somebody has the same problem? It only happens once, when I reboot everything is back normal. Most of the time it happens when my computer is shutdown for a few hours. After that a boot = low graphics mode, then reboot everything back normal.

---

### Post by christoph88 on 2008-12-03
Can't somebody please just give me a clue where I should start looking??

I completely reinstalled ubuntu. But it's still starting in safe graphics mode the first time I boot every morning. When I reboot it boots in normal mode with everything working...

---

### Post by deadowl on 2008-12-03
It sounds like it's more than likely a driver bug. Is it a restricted driver? From the manufacturer? Default?

I would try using an older driver version if it's from the manufacturer, or try unloading the restricted driver if you're using one and see if that fixes it.

---

### Post by christoph88 on 2008-12-04
It's a proprietary driver (NVIDIA accelerated graphics driver)
I got it from the hardware driver menu in Ubuntu.

I'm going to try to work with the older version and see if the problem is solved.

And thanks for your help

---

### Post by christoph88 on 2008-12-05
It was a driver bug,seems to be gone with the old driver. Thanks again for your help.

---

