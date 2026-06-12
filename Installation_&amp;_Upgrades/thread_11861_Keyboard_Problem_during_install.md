---
title: "Keyboard Problem during install"
date: 2005-01-19
forum: Installation &amp; Upgrades
---

### Post by masiemer on 2005-01-19
Ok,

At the very beginning of the installation where I am supposed to choose a language, the keyboard does not work.  I cannot move up or down or hit enter to select English.

I have an emachines M6809.  I know these are not great machines to install try to install linux on, but some other forum posts have shown that it has been done successfully.

I have tried using different boot options (ex. noapic noalpic bootkbd=es) and nothing has helped.

I had a similar problem attempting to install Gentoo linux, so I am assuming the problem is machine specific.  Has anyone with an emachines 68xx had similar problems?  Do I need to upgrade the BIOS somehow? 

Any suggestions?

---

### Post by rumleskaft on 2005-02-07
I have the same problem ](*,)  What to do  :shock:

---

### Post by rumleskaft on 2005-02-07
Maybe I'll have to say that I dont have an eMachine, but a Packard Bell iMedia...
But it still doesn't work, and yes! I have tried using both the ps/2, usb and a few other keyboards!

---

### Post by KiwiNZ on 2005-02-07
Have you got the correct keyboard settings in your Bios?

---

### Post by martijntje on 2005-03-14
[QUOTE=KiwiNZ]Have you got the correct keyboard settings in your Bios?[/QUOTE]
 A friend of mine has the exact same problem. It's also a Packard Bell. I don't think it has anything to do with the BIOS, because in the absolute beginning, you can press ENTER or F1 to start the install. It's only after it goes into the install menu that the keyboard stops working.

---

### Post by arie_maron on 2005-11-18
Hi People,

I had a similar problem with my USB keyboard on my computer (ATHLON XP 2200).

Try using the kbd-reset option at the boot prompt
i.e. "boot : * linux kbd-reset*".

It worked for me.

---

### Post by Thunderguy on 2005-11-18
Something else you might try in the bios settings, I'm on emachines that has the same problems, under USB mouse support somewhere, if you disable it, it might help, don't ask me why it's that though... I don't know why it would be USB mouse support, but that's what seems to work.

---

