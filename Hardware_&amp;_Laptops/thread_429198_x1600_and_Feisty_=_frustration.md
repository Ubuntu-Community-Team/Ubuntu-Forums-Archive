---
title: "x1600 and Feisty = frustration"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by Aaron_Henderson on 2007-05-01
I was wondering if someone could please help me get the ATI  (fglrx) drivers working.  I have been trying for over a week now, used every guide I could find, and no go yet.  I'm not sure why?:confused:   I just want 3d accel, I know beryl will not work and have no intention of installing it anyway.  If anyone could help I'd be eternally grateful.  I have read the x1300 thread below as well, before I am directed there...

---

### Post by Aaron_Henderson on 2007-05-01
Oh, system specs are : 

Sempron 64 3000+ @ 2.5GHz
1536MB DDR 454 @ 3-3-3-5
ASUS K8N-E (nForce3) newest bios, tried 32-512MB AGP Aperture
Sapphire x1600 Pro 512MB AGP

---

### Post by Aaron_Henderson on 2007-05-01
I once got "fglrxinfo" to display the proper info about my vid card, but when I dragged windows or scrolled up or down the window would distort kind of.  Really hard to explain.  If I can get it to that again than I will take screenshots and post 'em.  For some reason when I restarted though it reverted back to Mesa / Vesa and I didn't modify anything, so ???

---

### Post by olujicz on 2007-05-04
I have same ATI card, on Ubuntu 6.10 it works, but after upgarde to 7.04 ti just don't work. I try all how to on internet but they aren't help me.

I'm thinking to go back to 6.10.

---

### Post by mcduck on 2007-05-04
Here's easy instruction how to install Feisty with new X-series Ati cards: [http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194")

---

### Post by olujicz on 2007-05-04
I try. Still nothing.

---

### Post by mcduck on 2007-05-04
> **olujicz said:**
> I try. Still nothing.

What errors do you get when trying to install & configure the drivers using the commands provided in that link? They definitely work, I have X1600 on my laptop and running those commands was the only thing I had to do to get my card working with Feisty.

---

### Post by ericdegen on 2007-05-04
I think this is what I'm up against with my HP NC8430. Just now trying to load Feisty on it and can not even bring up the live CD, I'm a bit suprised by this as 6.10 worked great on the same box.

I'll follow the ATI related thread.

Eric

---

### Post by tim_za on 2007-05-05
Hey, you mentioned that when you restarted your config was changed.

I was looking around because of my ati x1600 problem and I found this bug which might be useful to you. [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/57716](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/57716).
It has something there that explains the restart thing, something to do with an entry that needs to be changed.

While I'm here, I'd like to know if anyone has experienced a similar problem to me, I'm using X1600 on an HP nx9420. I did a fresh install of feisty and when I chose the ati acceleration from the restricted modules check list (or changed it to the fglrx driver manually) My X server just hung on a blank screen and I couldn't get to any other virtual screens (not even terminal) I just had to crtl+alt+del to restart.
It works with vesa driver, vga works but doesn't seem to let gdm do it's thing (it at least shows a working cursor), and the fglrx hangs as explained.

---

### Post by Primoz on 2007-07-07
I have the same computer and can not get any special effects working.

Can somebody please tell me if it is possible to get desktop effects, beryl and similar
programs working on HP nx9420?

---

### Post by vooood on 2007-11-05
> **Primoz said:**
> I have the same computer and can not get any special effects working.

Can somebody please tell me if it is possible to get desktop effects, beryl and similar
programs working on HP nx9420?

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Install_Beryl_using_proprietary_FGLRX_drivers_from_ATI](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Install_Beryl_using_proprietary_FGLRX_drivers_from_ATI)

sorry for the late reply i just saw this..

---

