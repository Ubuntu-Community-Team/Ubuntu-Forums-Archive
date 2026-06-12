---
title: "HP 8440p GMA HD issues"
date: 2010-07-04
forum: Hardware
---

### Post by Wickd on 2010-07-04
Hi there

I just received my new HP 8440p laptop (GMA HD). I initially struggled to get Ubuntu 10.04 installed because of the black screen issue, which I solved by changing the grub boot parameters.

I added the following: "i915.modeset=0 xforcevesa"

This allows me to get to the login screen and I am able to use Ubuntu just fine.

I would however like to be able to use the aditional effects ie Compiz, which I cannot at this stage. I have looked all over the net for an answer, but cannot seem to find one that I can understand.

Can someone pretty please point me in the right direction? Attached is my Xorg.conf file. There is nothing in there, which I suppose is the problem :)

Thanks!

---

### Post by gordintoronto on 2010-07-04
Have you tried installing a video driver, from Administration/Hardware Drivers?

---

### Post by Wickd on 2010-07-05
Hi there

Yes I have. But it seems that a lot of the people are having issues with  this driver. That has not worked at all

Thanks

---

### Post by Wickd on 2010-07-06
bump...

---

### Post by gradinaruvasile on 2010-07-06
GMA HD is the Intel 4500 chipset?
If it is, it does not need and doesnt have proprietary driver. The only driver for it is the Intel driver that is already included in Ubuntu. Some newer versions may be installed from PPAs.
And normally you dont even need xorg.conf with the open source drivers, only if you want to mess around/tweak settings.

The xforcevesa command will force X to use the vesa driver - that is a basic driver that it is good only for debugging or as a fallback or very old+crappy cards.
You have to use the Intel driver if you want anything more.

PS. You did not attach the file...

---

### Post by Wickd on 2010-07-08
Hi there

This is a Intel Q57 chipset (Core i5)

Unfortuantely I need to force the Vesa driver otherwise the screen goes black while booting into the system. It looks like the intel drivers that is included does not work for this GMA?

Weird

Thanks

---

### Post by st! on 2010-10-07
hi,

i had the same problem with a blank screen on my HP  8440p. Is there any solution ?

---

### Post by ggarza78 on 2011-04-06
Have you solved this problem??? I have the same issue with a Dell Latitude E5510

> **Wickd said:**
> Hi there

This is a Intel Q57 chipset (Core i5)

Unfortuantely I need to force the Vesa driver otherwise the screen goes black while booting into the system. It looks like the intel drivers that is included does not work for this GMA?

Weird

Thanks

---

