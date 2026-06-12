---
title: "[SOLVED] H/W (ATI HD3650 and Audiophile 2496) upgrade results in severe problems"
date: 2008-10-29
forum: Hardware
---

### Post by Dragonath on 2008-10-29
Hello,

yesterday I replaced my ATI Radeon 9600 Pro for an ATI Radeon HD3650 (AGP cards) and also installed a M-Audio Audiophile 2496 sound card (having previously used the card integrated on my nVidia nForce 7NJS motherboard). Before the upgrade, my system worked quite well (Kubuntu 8.04 using KDE 3.59).
Now when booting up, these problems arose:
1) The USB stick with GRUB installed isn't recognized by the motherboard unless I boot into an old Kubuntu installation's console and do "fdisk -l" (I didn't test just booting the old Kubuntu without running "fdisk -l") and reboot. This may be caused by something else than the hardware upgrades, although I don't have any idea why (it occurs to me that I did move a power plug from a CD-ROM drive to the ATI HD3650, but does that effect anything?).
2) Booting into the -rt kernel (Ubuntu 8.04.1, kernel 2.6.24-21-rt) results in a seemingly endless cycle of some IRQ port garbage (ports 19 and 22 are mentioned I believe). About the same happens when I heed the advice and start the kernel with the "irqpoll" option (although then it seems to slow way down as it goes - maybe I should wait?). I read from these same forums that this card should work rather seamlessly with Ubuntu, so maybe it's got something to do with my ancient motherboard.
3) Booting into the generic kernel (Ubuntu 8.04.1, kernel 2.6.24-21-rt) sometimes results in non-working login dialog (I can't enter my password right because my keyboard produces weird characters) so I have to log in using the console and then start X. Once I get to my desktop where I am writing this from right now, there is no sound (a xine error pops up) and the screen resolution is set to 1280x1024 (on a 1680x1050 display). When I start the restricted drivers manager it tells me the ATI accelerated graphics driver is in use but not enabled (this is so even if I remove the fglrx packages and restart X).

Now I can live with the fact that I might need to downgrade my video card for the older 9600 Pro until Linux support for HD3650 comes available, however I would really like to know what's wrong with the motherboard not recognizing my USB stick right away as it used to and why my sound card is causing the rt kernel to go mad.

Thanks in advance and sorry for the long text.

---

### Post by Dragonath on 2008-10-29
Update:
I have now managed to get the video card working - fglrxinfo no longer shows me a MESA renderer, and I see no glitches or anything on the screen. I tried playing Urban Terror, which worked ok, but something crashed as I tried to exit it and I had to kill the process manually. However after that I couldn't move the mouse pointer anymore (maybe has something to do with xorg.conf, or thenagain caused by Urban Terror's crash).

My main problem now is that I still don't have any sound.

---

