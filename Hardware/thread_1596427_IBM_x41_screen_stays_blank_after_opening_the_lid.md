---
title: "IBM x41 screen stays blank after opening the lid"
date: 2010-10-14
forum: Hardware
---

### Post by lockalyo on 2010-10-14
Hey guys,

I have an issue with 10.10 - I configured the screen to go blank when I close the lid of the x41. When I open the lid, the screen stays blank.

Same thing happens if I press FN+F9 - screen goes blank and stays blank until restart.

Back on 10.4 I had the bug where when I open the lid, the cursor was gone. It had a workaround - pressing FN+F7 and the cursor was there. This time on 10.10 the whole screen disappears and no FN combination works.

I installed the 10.10 yesterday - clean install from USB with the whole hard drive formatted.

Does anyone have any suggestions?

---

### Post by Termo on 2010-10-14
I can confirm this bug as well on Thinkpad X41 (with the intel i915 chipset I think)... And I as well experienced the same issue on 10.04 with the cursor, that reentered after changing workspace.

I have tried to attach an external screen when the LDVS screen went blank (dimming the light still work?!?) and I was able to see my desktop on the VGA display. Using xrandr turning LDVS off and on did not change anything :(

---

### Post by Bradypodion Pumilum on 2010-10-14
Same here.  The regression first appears in kernel version 2.6.35-20 and might be related to LP #602281 (see [http://www.ubuntuupdates.org/packages/show/249235](http://www.ubuntuupdates.org/packages/show/249235)).

As a temporary workaround, linux-image-2.6.35-19-generic works fine for me. (Except of course for the disappearing cursor thing)

---

### Post by lockalyo on 2010-10-15
Yeah, I am back on 2.6.35-19 and only the cursor disappears - way better than the whole screen :)

Just wondering, it is worth submitting this as a bug or...

---

### Post by Termo on 2010-10-15
How do you downgrade to 2.6.35-19??

In the PPA's I have I can only find 2.6.35-22 when looking for linux-headers...

---

### Post by lockalyo on 2010-10-19
Well, I downloaded the .deb file of the -19 and installed it (double-click :D). After that I put on GRUB and now I can choose which kernel to boot with.

---

### Post by Termo on 2010-11-24
BUMP!!

Just installed the latest kernel 2.6.35-23, which had a lot of fixes for the i915 - but still same issue :(

Any ideas??

---

### Post by bronevaya on 2010-11-26
this thread topic is my homepage. any new news?

---

### Post by lockalyo on 2011-02-01
I am now with 2.6.35-25-generic and the problem still persists. Killing X does not help as well.

---

