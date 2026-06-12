---
title: "[resolved] sound not working after new kernel"
date: 2004-12-16
forum: Hardware &amp; Laptops
---

### Post by vontez on 2004-12-16
I just installed a fresh 2.6.9 kernel from kernel.org, because I want to get my SD card reader working.  Everything seems to be working just fine except for the sound.  I built my snd_intel8x0 driver directly into the kernel so I don't think it is a problem with the kernel build.

The funny thing about it is that when Ubuntu first starts and shows the login screen, the little drum sound plays through my speakers.  After I log into Ubuntu, there is no sound whatsoever.

Any Ideas?

Edit:  Oh yeah, I forgot to add that I completely removed OSS from the kernel.  I thought Ubuntu used ALSA, could this be the root of the problem?

---

### Post by vontez on 2004-12-16
Well, after remembering that I had not included OSS in the kernel, I recompiled my kernel with support for OSS and my driver, and my laptop sound is running fine now.

---

### Post by cyb on 2004-12-16
Hey, I have exactly the same problem, but I didn't do anything with my kernel at all!
After I installed Ubuntu, I installed Acrobat Reader, the nVidia drivers, and I mounted my NTFS partitions, and then I rebooted. 
When I started Ubuntu again, I can hear the little drum, but as soon as I log in there's no more sound, nowhere! :(
Can anyone help me? Or can you tell me how to recompile a kernel with OSS support? :P
BTW, my sound card is onboard, a Via82xxx or something.

---

### Post by vontez on 2004-12-16
I marked this post as resolved, so for the best results you should repost your question in the forum.  Also, list your output of lspci ($ lspci) and the output of lsmod ($ lsmod).  This will help everyone in the forum figure out your problem.

Hope this helps!

---

