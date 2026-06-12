---
title: "Upgrade 9.04 to 9.10 gives blank screen."
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by hxc-riot on 2009-11-01
Hey

I've upgraded my system from 9.04 to 9.10 and now it gives a black screen after the grub menu. When I choose to startup in recovery mode (netroot) and then type ´startx´ it works and it will startup gnome.

System specs:
3.0 Ghz P4
2GB DDR2 Dual Channel
ATI x740xl

I tried to run the `sudo dpkg-reconfigure -phigh xserver-xorg` command in recovery mode but with no results.

Does anyone has a solution?

Greetings,
HxC-RiOT

---

### Post by jim_60525 on 2009-11-01
Yes, I've had exactly the same problem.
Had 9.04 running on a Compaq Evo1015n. Upgraded to 9.10 and when restarting got the blank screen after GRUB.

---

### Post by hxc-riot on 2009-11-02
Now I did a fresh install of 9.10 but I still have the same problem, a blank screen after the grub menu. So it isn't the upgrade.

Are there more people experiencing the same problem? Or does someone has a solution / suggestion?

---

### Post by bartvdm75 on 2009-11-02
i also have the same problem...
first upgraded from 9.04 tot 9.10..
i could use the 9.10 with the 3third kernel in grub, although all was very slow..
after fresh install, i still had a blank screen...

now i'm on 9.04 again..

Acer Aspire 5783Z
4Gb DDR3
15.6" HD LED LCD
Intel T4200 processor
Intel GMA 4500M video

please help !

ps : 9.10 works very good on my old desktop computer..

---

### Post by vivekanands on 2009-11-02
Same problem here.
I upgraded my Kubuntu 9.04 to 9.10 and after the installation I rebooted, and am just getting a blank screen.

Grub hasn't changed my boot entry, as the default entry was and continues to remain Kubuntu 9.04.

Please help. I hate to use windows at home, have enough of it at office!

PS: 1> My Laptop config is as under
Thinkpad R52, Intel Pentium M 1.7 Ghz. 512 MB Ram - mostly DDR2, IBM Thinkpad 17" LCD panel with an Intel 915GM/GMS display capable of supporting 1024x768 @ 85 hz.
2> I am not a fundoo user, so please elucidate as much as possible

---

### Post by hxc-riot on 2009-11-02
I got my ubuntu started, but it's only a workaround!
1. Start ubuntu in recoverymode (Grubmenu)
2. Choose netroot.
3. Type: login yourusername
4. Type: startx

I also hope to conclude that the grub config is somehow wrong, or something with the login manager?

---

### Post by bartvdm75 on 2009-11-03
and this works ??

---

### Post by skyiscrying on 2009-11-03
I had to do a re-install of Karmic and opted for ext3 file system when partitioning. After this I still had a blank or black screen until I selected "none" in *system - preferences - appearance - visual effects*. Then as if by magic, there was the default Karmic screen, and my USB stick icon. I must add that my graphics card is about 7 years old - well so is most of  the whole computer.

---

