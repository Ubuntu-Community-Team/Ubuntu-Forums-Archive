---
title: "Black screen on boot with Radeon laptop"
date: 2011-02-11
forum: Hardware
---

### Post by MrNatewood on 2011-02-11
Hello,

I have Ubuntu Maverick installed on a Dell Studio 1555 laptop with a Radeon HD card.

3D games were not working and also when tring to enable compiz effect it complained that I don't have supoorted drivers installed.

So I tried the following:
Went to Jockey, saw that "ATI Fire GL" was enabled. Disabled it.
Went to Synaptic. Re-installed fglrx and while I was at it ran a full system upgrade(mark all updates).

Rebooted.
Now I get the ubuntu loading screen, then it goes blank, I hear the ubuntu cicking login screen sound, but I dont see anyhting on the screen. It's all purplish-black and no gdm.
If I try to press ctrl+alt+F1/F2 I get a 100% blank screen(not purplish anymore) and no command line of any sort.

Does anyone know how to get back screen output without re-installing Ubuntu?

Edit: solved through using a live USB to make a xorg.conf(none existed before) file with a known good configuration.

---

