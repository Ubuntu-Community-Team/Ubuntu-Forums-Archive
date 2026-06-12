---
title: "Ubuntu is using a lot of RAM"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by short4lif2 on 2005-10-26
I may be a complete newbie and just don't understand what I am seeing but in ubuntu, 78% of my memory is being used, of which 47% is cache and all i have open is gaim and firefox.  Does anyone know what is going on?

---

### Post by aysiu on 2005-10-26
Sounds as if you may have 256 MB of RAM or less.
Otherwise, there's something wrong.

---

### Post by short4lif2 on 2005-10-26
I have 512.  When i open the system monitor it says so.  But now i realize that in the system monitor it says i am using 29.2 % of my ram... while in the system monitor in my panel it says i am using  89% now.

---

### Post by jrw6 on 2005-10-26
Linux is fairly aggressive at caching things into RAM.  If you're not using your RAM to have programs open, Linux will start caching things from disk that you "might" open soon into RAM.  This will have the effect of making it look like you don't have much free memory.

---

### Post by aysiu on 2005-10-26
Don't forget that Firefox is a memory hog, no matter what operating system you use.

---

### Post by Leopard on 2005-10-27
[QUOTE=jrw6]Linux is fairly aggressive at caching things into RAM.  If you're not using your RAM to have programs open, Linux will start caching things from disk that you "might" open soon into RAM.  This will have the effect of making it look like you don't have much free memory.[/QUOTE]
The cached stuff in your RAM will be dropped if you open more programs, it's just to save time in case you open the program that is already cached.

I believe it is apps that you have already opened previously in this session.

---

### Post by learner on 2005-10-29
Hi, guys. I have been having same problem lately, i run gnome and the memory consumption wasn't that high, about 230mb. but occasionally, it freeze or hang for a moment. when i switch to kde, it is worst, the memory consumption was about 450mb, which was when i am not using anything at all, i can hardly believe my eyes. have anyone come up with a solution to this. it happens after i  install some theme, but now, when i not using those themes, the result is the same. 

I am using a toshiba a70, and so far, this is the best distribution that detects all of the hardwares.

---

### Post by frenkel on 2005-10-30
Linux tries to use as much RAM as possible, empty RAM == useless RAM.
Loading things in RAM speeds up stuff very much. Untill apps get killed and messages like "out of RAM" appear, there's no need to wory!

---

### Post by learner on 2005-10-30
Hey, thanks Frankel, do you know if there is a way to optimize linux. sometimes, when i am running multiple applications, it tends to hangs a bit.

---

### Post by frenkel on 2005-10-30
Learner, What is the output of sudo hdparm /dev/hda ?

---

### Post by learner on 2005-10-30
here is my output from sudo hdparm /dev/hda:

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 156301488, start = 0

Strange enough, this morning when i reboot my laptop, it hangs at the word reboot, and then all the words is in screen is scrambled. i notice that after the line reboot, there is another line with "[some decimal numbers] reboot". this is the first time i have ever seen this line.

---

### Post by frenkel on 2005-10-30
Mm, DMA is on, so that shouldn't be the problem. What kind of processor do you have and what programs are you talking about?

---

### Post by learner on 2005-10-30
I have a P4 3.06Ghz, 512mb of ram, with 64mb shared ati radeon 9000(which ubuntu recognized as 9100, but still work since it use the ati driver from xorg.) and a 80gb 4200rpm hd. 
i uses a i686 kernel in breezy. Actually, i uninstall some apps, and it fixed the often hang or freeze problems, but, i still have performance problems when i start multiple apps, like firefox, gaim, evaqq, and scim(self-build, due to the fact the one with breezy is broken). And new problems is starting to coming in, ( like the reboot in my last post.

---

