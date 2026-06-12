---
title: "crash - half screen blinking ascii stripes"
date: 2010-09-09
forum: Hardware
---

### Post by naxa on 2010-09-09
hi! 10.04 minimal install with openbox. randomly my system crashes and screen goes back to CLI but with the whole constantly blinking like it tries to adjust the resolution. then i see half of my screen filled up with vertical stripes made of the "full" ascii character and blank spaces. the lowe half is completely blank. i have an old integrated intel graphics card (i think 82845G/GL/GE/PE/GV). my comp is dell optiplex gx-260. above the core system, ardour, openbox, cups, sshd, gdm, jack, alsa, X, links and arora + small stuff like xterm etc. is installed.

when i first tried to logon the screen was half blank and the upper half was filled with gdm buy it was strangely distorted and interlaced

p.s.: I saw others have similar problems on other dell machines with this card, and some of they attributed the problem to firefox. this cannot be true (at least in my case), since i had no firefox installed.
only recently i installed firefox and pidgin, but the crash occoured long before that.

p.s. 2: most often it occours in the first 30 minutes after booting, randomly. no keyboard or mouse input is accepted. the hdd led blinks only a very little bit (1 / 10-20 sec)

---

### Post by Joe of loath on 2010-09-09
I've got exactly the same problems on my GX60 with the same graphics, running Lubuntu.

---

### Post by naxa on 2010-09-11
I've installed another kernel (2.6.33, a realtime-pae version btw).

Now when the crash happens, I still am able to use the command line interface. However, I cannot restart X nor gdm. I still end up with rebooting, but now I can do it from ubuntu command line instead of the power button...

Many thread has this problem with old graphic cards. For example:
[http://ubuntuforums.org/showpost.php?p=9830905&postcount=45](http://ubuntuforums.org/showpost.php?p=9830905&postcount=45)

I don't really want to use the vesa driver, but will try the other workaround. However, even if it works, it's only a workaround, not a fix... Still, I hope it will work.

---

### Post by naxa on 2010-09-12
I've tried the solution mentioned in the above link, and it DIDN'T work for me.

Actually it made things worse, since now I don't get the CLI even with the new kernel, only a blinking/flickering screen.

Still waiting for the solution...
Meanwhile, could anyone help me to fill this as a bug in launchpad? I don't know how should I do it..

---

### Post by naxa on 2010-10-03
I found 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
and "GTT Incoherency Patch" combined with "Workaround A: Re-enable KMS" and also editing /etc/default/grub file's GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to do NOT include the i915-whatever=1 or 0... thing, it helped.
I must note that I use a 2.6.33 real-time pae kernel, not the original one. I don't know if this matters or not.
My system is pretty stable this way. However, I left my computer turned on and alone for 2-3 hours and the screen rendering "speed" was very bad after I came back. Well actually not the whole rendering, as the mouse moved very normally.*

I logged out and the logged in again, and this fixed the screen speed. If I can only find out what maked it slower in the first place...


*:
However, for example if I moved the terminal window, the move was made in distinct "steps", not like it normally "flows"... Also when I typed into the terminal, strange things happened, sometimes it wasn't when i backspaced things, not all characters disappeared, but they effectively wasn't there since i pressed enter and it acted like if there was nothing there. However I could still see the characters remaining... this was also the case with other windows, like pidgin.

---

