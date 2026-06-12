---
title: "No sound with Intel VIA VT1705 onboard card"
date: 2011-09-17
forum: Hardware
---

### Post by GordonGR2011 on 2011-09-17
Hallo everyone. I'm not a new Linux user, but hadn't had sound issues since 1999, so for all intents and purposes, I am a newbie.

I have a custom-made desktop, with an onboard Intel sound card. The card worked perfectly with Debian Testing (32bit, though), so it's not a hardware issue. Since I installed Natty two days ago, I have no sound. I have checked the obvious (volume, cables etc), they're all fine.

My alsa information is here: [http://www.alsa-project.org/db/?f=06c0fbbdc0554b8f9d53f731d47e6af93925c47a](http://www.alsa-project.org/db/?f=06c0fbbdc0554b8f9d53f731d47e6af93925c47a) . The “snd-hda-intel: model=auto” module you'll see wasn't set during installation, I set it myself following advice from here [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) , but it didn't work. Also, I tried installing drivers from here [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules) , but it didn't work either. 

Any help will be greatly appreciated!

Thanks!

---

### Post by ubudog on 2011-09-17
Moved to Hardware & Laptops.  Hopefully you can get some more answers here.  :)

---

### Post by GordonGR2011 on 2011-09-18
I experimented a bit more, trying kernel 3 using the instructions here [http://www.khattam.info/howto-install-linux-kernel-3-0-in-ubuntu-11-04-natty-narwhal-2011-06-03.html](http://www.khattam.info/howto-install-linux-kernel-3-0-in-ubuntu-11-04-natty-narwhal-2011-06-03.html) , but it didn't work. Then I followed my friend Koleoptero's advice and checked how proper (Gnome) Ubuntu works and… it works fine! So I returned to Ubuntu. It must be a bug. Thanks anyway.

---

