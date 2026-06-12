---
title: "scrollbar erratic 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by flaflashr on 2009-11-06
Kubuntu 9.10 on Dell D600 laptop fresh install from DVD

I have been using Kubuntu on this machine since 8.04.  I did a fresh install on a clean disk from a DVD I downloaded.  I applied all of the updates available.

In several (maybe all?) applications, Firefox, KPackagaKit, Konqueror, when I scroll by using the mouse on the right scrollbar, it works fine for a couple of clicks, then the takes off and uncontrollably scrolls to the end of the page (or top, depending on which direction I was going.)

When I put the old hard disk with 9.04 in, it goes back to normal.

I searched here, but did not find any hits.

Thanks for your help.

---

### Post by edin9 on 2009-11-06
Do you have a Synaptics touchpad?

---

### Post by flaflashr on 2009-11-06
I suspect it might be a Synaptics touchpad.  I don't remember it being a Synaptics touchpad, but it could be. The BIOS setup does not mention.

I checked using the old disk with 9.04, and it had a Synaptics driver installed (0.99.7 I think).

The new disk with 9.10 has xserver-xorg-input-synaptics-1.1.2.1ubuntu-7 already installed.

Guessing where your lead might go, I tried installing the gsynaptics tool, however, it does not seem to have made much, if any difference.

Suggestions?

---

### Post by hviertol on 2009-11-06
This is a reported regression bug on ubuntu 9.10, see [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/444674](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/444674)

---

