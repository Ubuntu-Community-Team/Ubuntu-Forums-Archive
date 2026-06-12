---
title: "driver problem"
date: 2010-09-17
forum: Hardware
---

### Post by notice on 2010-09-17
hello 
 
i recently bought a HP g62-a31 computer. It is running win 7 and ubuntu 10.04. in the beginning everything was ok, but then ubuntu suggests to update the ati/amd driver. And i was stupid enought to do the update. After a reboot into ubuntu the screen goes completely blank. When I try to start in recovery mode the screen is still blank.
Only when I press "e" in  the start of recovery mode I can see a kind of terminal with the word grub>
What can i do to get rid of the driver?

---

### Post by dougalkerr on 2010-09-17
There is a work around for this somewhere. It means copying a good xorg.conf file over the bad one if I remember correctly.
Do a google for 'replace' xorg file to return to default...

And don't do it again. There is a little warning about using the propriety drivers.
Having said that it is a good learning curve. I bet a lot of us have been there and done that.

I have Ultimate Edition installed and have tried the driver suggested and it didn't work as expected but, I was able to recover and disable the driver within the system.

Maybe changing to Ultimate Edition might work for you too.
It is a big download though but, full of preloaded software and very customizable.

---

### Post by notice on 2010-09-17
But the problem is how du I kill the grafic interphase or somehow get to a terminal to be able to do the uninstall

---

### Post by dougalkerr on 2010-09-17
Do a search for how to recover X. I don't know off-hand but, there is definitely a fix.

Post again with this in the title: How do I recover X?

---

### Post by Toz on 2010-09-17
You need to boot into recovery mode. When the computer is booting, hold down the shift key and it will display the grub menu. Select the option that ends with (Recovery Mode). This will take you to a "Recovery Menu". Scroll down and select the root option. This will drop you to the command prompt in recovery mode (no X).

A possible quick fix may be to recreate the xorg.conf file. Type in:

   aticonfig --initial -f

When this completes, type:

   reboot

to reboot the computer. See if that helps.

---

### Post by notice on 2010-09-17
yes I can reach the Grub menu and select the recovery mode, but it also ends up in a blank screen.

---

