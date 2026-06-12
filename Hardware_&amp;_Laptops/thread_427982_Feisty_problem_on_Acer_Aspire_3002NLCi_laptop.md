---
title: "Feisty problem on Acer Aspire 3002NLCi laptop"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by Frozen Fire on 2007-04-29
I have installed feisty on my Acer Aspire 3002NLCi laptop and it works flawlessly, but after I look around and trying Mplayer, I noticed that Mplayer can't play in Xv mode. I looked at xorg.conf and changed "vesa" to "sis". It helped much, I can view movies with Mplayer with Xv mode and fullscreen. Then the night comes and I want to shutdown my laptop, and the problem begins. If I use vesa, the ubuntu usplash shutdown screen shows up, but if I use sis, the shutdown progress shows in a console mode. Why?

That's the first problem. The second is if I let my laptop idle, it just went blank to screensaver and never goes standby/hibernate even if I reconfigured the power management setting. But if I press the button standby/hibernate, it goes to sleep successfully. Why feisty can't go to standby mode automatically after idle for  a periode of time?

Well that's all my problem, hope someone will help me soon.

Thanks

---

### Post by Frozen Fire on 2007-04-30
No one shows up? Please help!

---

### Post by Frozen Fire on 2007-04-30
First problem solved by adding line 'vga=791' add kernel parameter in grub's menu.lst, I follow the hint from this link [http://ubuntuforums.org/showthread.php?t=212832](http://ubuntuforums.org/showthread.php?t=212832)

Now goes to second problem, how come feisty can't detect whether the laptop is idle or not?

---

### Post by Frozen Fire on 2007-04-30
Second problem solved by reinstalling gnome-screen-saver, set idle 1 minute at screensaver and set the rest via gpm

---

