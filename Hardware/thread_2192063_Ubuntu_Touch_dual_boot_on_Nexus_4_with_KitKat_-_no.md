---
title: "Ubuntu Touch dual boot on Nexus 4 with KitKat - no sound, no mic"
date: 2013-12-05
forum: Hardware
---

### Post by trombipeti on 2013-12-05
Hi,
I've managed to get Ubuntu Touch and Android KitKat dual boot on my LG Nexus 4. Currently I'm using the factory android 4.4 image, and the v32 utouch image from the devel channel (trusty). I got dualboot working with MultiROM Manager. I installed a modified stock 4.4 kernel with kexec-hardboot patch with multirom, and I know that there is some incompatibility with it in terms of wifi (it is not working, to be short).
However, the biggest problem is that I cannot get audio from and to the device. More precisely, neither the speakers nor the mic work. I cannot play music, cannot hear anything during calls and the person I'm calling cannot hear me either.
I opened up a terminal on utouch and opened alsamixer. What I can see is that it says: Speaker Item [Off]. However badly I press 'M', it stays the same.
I'm guessing that there is some kernel module problem. Can this be the cause? If it isn't, what else could be? Either way, is there anybody else experiencing this issue? How can this be resolved?

Thank you for your help!
Peter

---

### Post by trombipeti on 2013-12-10
Anybody?

---

### Post by surc on 2014-01-04
I had the same issue happening to me. You probably have to downgrade the android radio. You can follow the steps here: [https://wiki.ubuntu.com/Touch/DualBootInstallation#Android4.4Radio](https://wiki.ubuntu.com/Touch/DualBootInstallation#Android4.4Radio) (Where it says "Follow the links in this table" and doesn't show any links, I just googled "Nexus 4 4.3 firmware", and downloaded the proper .tar from the official android page)

The one thing that had me hung up for a minute is that when it says "reboot ubuntu", it didn't seem to be working, and I couldn't figure out why. Turns out I had to open the "Ubuntu Dual Boot" app *in Ubuntu* and tell it to reboot into Ubuntu again.

Edit: Also, forgot, another little weird thing that happened to me is I was still getting no audio until I actually went into the sound settings and changed a ringtone, at which point it played the ring tone correctly and started everything working.



If you're still having this problem, hope that works for you!

---

