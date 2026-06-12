---
title: "Can only install in &quot;safe graphic&quot;"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by willypermana on 2008-12-09
So the CD I requested from ShipIt has arrived. I immediately installed it on my box. The installation went smoothly, but upon restart, after the loading bar it just went black. No respons at all.

I tried re-install it. This time in "safe graphic" (F4 on install menu). After the installation, I can logged in into Intrepid, but I'm stuck on 800x600 resolution. Not pretty. The only other option is 640x480.

I gave up and switch back to 8.04. But I do want to try install Intrepid again. Any suggestion how I could log into 1024x768 screen ?

Oh, and there's also this problem. Whenever I put 8.10 CD on 8.04 system, I can't eject it from the CD drive. First I have to unmount the CD as root, only then I can eject it. Anyone runs into the same problem ?

---

### Post by jedi-penguin on 2008-12-09
Not sure about the CD drive thing, but the black screen and resolution problem could relate to your graphic card. If you use Nvida, install nvidia-setting and nvidia-xconfig. Intel used a differen one, I don't remember.

---

### Post by MeURi on 2008-12-09
Exactly, this could be an issue with you graphics driver, and probably a misconfiguration in the Xorg.conf file.

Install the proper drivers and everything should be ok.

---

### Post by willypermana on 2008-12-12
The problem is, I'm using "generic" onboard graphic card. Don't know which brand it is (my guess is VIA).

Anyway, thanks for the suggetions. I'll check the xorg.conf when I get the chance.

---

