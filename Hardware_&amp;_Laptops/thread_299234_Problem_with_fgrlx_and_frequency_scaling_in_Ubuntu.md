---
title: "Problem with fgrlx and frequency scaling in Ubuntu"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by nappleapple on 2006-11-13
The last time I installed the ATI fglrx drivers, something screwed up and I had to go through a lot of mess to fix it.  But everything worked afterward.   Then apt-get decided to update my fglrx drivers for some reason, and that broke my fglrx drivers.

After that, I had problems whenever I'd try to run glxgears or anything that involved 3d acceleration, my computer would completely lock up and nothing would respond except the mouse (which didn't do me any good).

So I decided to reinstall the fglrx drivers from ATI using the kernel module solution.  When I restarted my computer, however, I noticed my fan was constantly running.  I check out my "CPU Frequency Scaling Monitor" which tells me my processor is running at 100% (1.8 GHz).  I tried changing it, but the only governor which is selectable is performance which is always selected.  And the frequency selection shows the frequencies which my processor can operate at...but "Automatic" is selected and selecting a different frequency produces no change.

I'm thinking that the ATI driver installation had something to do with it, but I'm not sure what because when I switched back to using the xorg provided drivers, I still couldn't change the frequency. :-k 

Recap: Reinstalled fglrx driver, "performance" only frequency scaling started after installing the fglrx driver, switching back to the "ati" driver doesn't fix.

Does anyone know why this is?:-?

---

