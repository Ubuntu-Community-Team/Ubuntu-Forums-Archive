---
title: "Upgrade From Intrepid To Jaunty Broken OS Now!"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by nshiell on 2009-06-08
Hi I use XUbuntu for a pc at home (AMD Athlon)
I went to use the GUI tool to upgrade XUbuntu.
Apart from an issue upgrading PHPMyAdmin the update finnished.
However when I boot up the PC it boots fine then after about 1minute the whole system hangs every time - the mouse dosn't move, you can't toggle num lock etc...

I did a live boot of Juanty (off CD) and it loaded fine, I chroot'ed into the OS drive and did apt-get upgrde, update etc, but that didn't help.

Bit of a noob here, so unless I can figure this out I'm gonna have to zap the OS drive, which I realy don't want to do.

Please any ideas much welcomed!

---

### Post by sendblink23 on 2009-06-08
Does in the boot of Xubuntu.. do you have the choice of choosing any older *versions (before the upgrade)? Upon Computer start Up .. in Grublist..?

---

### Post by nshiell on 2009-06-08
Not sure what you mean, don't know about GRUB, can you explain?
P.s. the boot seems normal - no command line prompts
Thanks

---

### Post by nshiell on 2009-06-09
After allot of cursing, i finnaly got it to boot freeze and flash caps lock and scroll lock LEDs.

So I rearranged the RAM and it seems a little more stable.

There is something the Kernal dosn't like about my motherboard I guess.

---

