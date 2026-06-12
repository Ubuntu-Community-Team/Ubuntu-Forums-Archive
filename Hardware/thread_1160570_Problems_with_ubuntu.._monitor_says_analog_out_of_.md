---
title: "Problems with ubuntu.. monitor says analog out of range!"
date: 2009-05-15
forum: Hardware
---

### Post by leamons on 2009-05-15
I recently replaced windows XP with Ubuntu 9.04, and even since when I turn on my computer it displays a message saying "analog out of range" for about 15 seconds. After that it will either continue to boot up ubuntu, or not do anything and force me to turn of the computer by the power button. I read on some other forums that it could be because I don't have any graphics driver installed. My video card is integrated and it is an ATI xpress 200. I looked in add/remove for a driver, and found ATI catalyst, and the ATI site said it was the right driver. Now that I go back into add/remove, I can't find anything related to ATI. I tried downloading it from ATI's website, but it is .run, and I have no idea how to install this.

Do you guys think it is because of having no grahpics driver? If not how can I fix this?

Note: I have noticed that when I turn on my PC, it says that loading grub message, then it says "unknown header type 14, ignoring", then it continues to either show the message and boot up or show the message and do nothing.

---

### Post by lisati on 2009-05-15
I think it's a screen resolution issue: I had a similar error message about "signal out of range" when I had "Standard" Jaunty on my main desktop. The way I dealt with it at the time was by modifying grub's menu.lst file to not show the splash screen while booting. If memory serves correctly there are other options as well, but I never bothered researching them fully.

The interesting thing I've noticed is now that I have Ubuntu Studio 9.04 on that machine instead, the splash screen shows perfectly. I suspect that it uses different default settings.

EDIT: P.S. I think the machine I had the error on has some kind of ATI-based system too.

---

