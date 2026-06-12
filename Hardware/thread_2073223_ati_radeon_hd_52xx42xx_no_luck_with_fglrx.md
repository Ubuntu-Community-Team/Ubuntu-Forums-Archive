---
title: "ati radeon hd 52xx/42xx no luck with fglrx"
date: 2012-10-19
forum: Hardware
---

### Post by magowiz82 on 2012-10-19
My notebook has got a video card with a sort of double gpu processor, in short is like I have 2 different video cards.

In ubuntu 12.04 the situation was : with legacy fglrx driver (12.6) I can use internal notebook display but no luck with hdmi output, with fglrx 12.8 or 12.9 I can use hdmi out but internal monitor is disabled and there is no way to use it.
What I understood is that the hd 52xx manages hdmi out and hd 42xx manages internal notebook display and it seems that choosing one driver version or the other excludes one of the gpu. 
In the end I choose to forget about hdmi out and use legacy driver (12.6) to be able to use mine notebook display.

This until 12.10 upgrade : legacy driver doesn't work anymore and I was able to use internal display only with radeon (open source) module.

That said I would like to ask you if there's a way having both hdmi out and internal display working at the same time like duplicated screens (in windows it works like this) or I should give up and be glad that at least I can use my notebook screen?

Please tell me if you need further info and I will provide it.

---

### Post by buckyaustin on 2012-10-19
There was an update released today for graphic drivers. So lets get your drivers up to date hopefully before looking at some serious problems. Type this in terminal. "sudo apt-get install update && sudo apt-get upgrade". Then check if you can turn on both at once. If the drivers work correctly then you should be able to do this. Because this works for me and I use the same driver. 

Use a GUI for Monitors. It is located in system settings. If you can't do it through the GUI please report your findings here.

---

### Post by magowiz82 on 2012-10-19
thank you for your quick reply, I forgot to say that I upgraded to 12.10 this morning, anyway I gave the commands you give me and I (re)installed fglrx, the situation is the same (only hdmi out, no internal display), I restored previous situation removing fglrx and deleting xorg.conf (created by using aticonfig --initial --adapters=all -f). 
I was also able to read devices information in amdcccle and like before I can only see one gpu : hd 5000 series .

---

### Post by buckyaustin on 2012-10-19
You should be able to do it through the AMD Catalyst Controller. That's what I use instead of the default monitor settings in system settings. Sometimes the administrator program doesn't work if that is the case use "gksudo amdcccle". Then you should be free to test/change settings.

---

### Post by magowiz82 on 2012-10-19
> **buckyaustin said:**
> You should be able to do it through the AMD Catalyst Controller. That's what I use instead of the default monitor settings in system settings. Sometimes the administrator program doesn't work if that is the case use "gksudo amdcccle". Then you should be free to test/change settings.
I'm sorry but I can't , current fglrx doesn't detect my radeon hd 4200 series so with the amdcccle I'm able only to tweak settings for hdmi out display and another external display, due to the fact that is 4200 series gpu that controls my internal laptop display I cannot do it.

---

### Post by QIII on 2012-10-19
The HD 4XXX series cards and earlier have been moved to a legacy driver branch in Linux.  Unfortunately, that branch does not support X Server 1.3, which Quantal uses.  The 12.9 "Ubuntu preview Beta" supports X Server 1.3 (sort of), but not chipsets prior to the HD 5000 series.

P poor support on the part of ATI when those cards are still on the shelf, even if ATI only has a skeleton crew on doing Linux development.

I've been NVIDIA/ATI neutral for a long time, but this may put a stop to that.  And I'll have to get around to updating the wiki, I suppose.

---

### Post by magowiz82 on 2012-10-19
the problem is the fact that in my notebook I've got 5xxx series which is the earlier chipset supported by current drivers but it seems not supported by legacy and 4xxx series that is the opposite (legacy supported, current unsupported). 
I start to think that there is no way out in my particular situation to get them both working under linux.

---

### Post by QIII on 2012-10-19
You can try the open source Radeon driver and vgaswitcheroo.

---

### Post by magowiz82 on 2012-10-19
> **QIII said:**
> You can try the open source Radeon driver and vgaswitcheroo.
thanks for the tip, I searched for this package but I cannot find it, is it from a PPA ?

---

