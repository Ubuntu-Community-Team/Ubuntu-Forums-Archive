---
title: "New LinkSys WiFi Card Problems"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by zinchalk on 2005-05-14
Hello, I just recently installed and purchased a Linksys wireless network system from good ole circuit city. I installed the wifi router on my windows box downstairs, and installed my wifi card in this pc (winXP/linux box) and everything went smoothly for windows (because it came ofcourse with xp drivers) so i reboot and log into linux hoping it would be as easy but, its not detecting my card.

I have never installed or removed hardware from my linux box before so i dont exactly know how to handle the situation. I just thought it would auto-detect the card and then i would just set up my wifi with the networking daemon.

So, can someone tell me how to correctly setup my card for linux (or how to auto detect for future knowledge) or could they just point me in some direction in which i am doing wrong.

thanks!

---

### Post by jkndrkn on 2005-05-25
Try this:

[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

---

### Post by Staesys on 2005-05-25
What is the model of linksys card, and chipset (if known)?

Have you looked in the device manager to see if it at least is shown as being detected? even if the driver isn't loaded, There should be a mention of it and the chipset in the device manager.

---

