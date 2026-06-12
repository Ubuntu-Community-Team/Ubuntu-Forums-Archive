---
title: "ati X1600 slow on Lucid"
date: 2010-06-26
forum: Hardware
---

### Post by neonic on 2010-06-26
Hello, I have a pc with an ATI Radeon X1600 pro graphics card. I have both windwos XP and ubuntu 10.04 installed. The problem is this: on windows, the graphics are always fast. On ubuntu, many applications have terribly slow graphics.

Even the aisleriot solitaire card game runs with slow graphics, though I notice no problems with flash applications on the web.

On windows, I have the official driver from the CD installed, but on ubuntu this is impossible. There appears to be an open source driver installed and there's something called 'KMS' switched on it seems.

Can someone help me making ubuntu's graphics run better?

Thanks!

---

### Post by efflandt on 2010-06-26
I have probably somewhat older ATI X1300 and not only noticed sluggish default video in 10.04, but also suspend and hibernate did not work, because it would never shut off my video.  I noticed card trails in Solitaire and glxgears (mesa-utils) was very slow and jerky.

But the generic **nomodeset** (or ATI specific **radeon.modeset=0**) kernel boot parameter to disable KMS brought video up to 9.10 speed and fixed suspend/hibernate.  Although, I occasionally have a resume issue in 10.04 (hangs with flashing Caps Lock and Scroll Lock on keyboard), so I have been using hibernate instead.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

---

### Post by neonic on 2010-06-26
> **efflandt said:**
> I have probably somewhat older ATI X1300 and not only noticed sluggish default video in 10.04, but also suspend and hibernate did not work, because it would never shut off my video.  I noticed card trails in Solitaire and glxgears (mesa-utils) was very slow and jerky.

But the generic **nomodeset** (or ATI specific **radeon.modeset=0**) kernel boot parameter to disable KMS brought video up to 9.10 speed and fixed suspend/hibernate.  Although, I occasionally have a resume issue in 10.04 (hangs with flashing Caps Lock and Scroll Lock on keyboard), so I have been using hibernate instead.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture")

I have added "nomodeset" to GRUB_CMDLINE_LINUX in  /etc/default/grub and I ran "sudo update-grub", first the video didn't get any faster.

After I rebooted ubuntu however, the graphics were suddenly a lot faster. Many thanks!

However, I wonder if disabling KMS has any disadvantages.

---

### Post by icelos69 on 2010-07-19
using the nomodeset option, i gain accelerated graphics (beautiful, really), but I lose S-video out for some reason.  Xrandr doesn't even detect it.  Any ideas?

---

### Post by stefanos6991 on 2011-08-24
LOL THAAAAAAAAAAAAAAAAAAAAAAAAAAAAANK YOUUUUUUUUUUUUUUUUUUUUUUUU SO MUCH! HAD PROBLEM WITH MY CARD LIKE 2 YEARS Always used to migrate to ubuntu and back to windows for its so bad support of ati! (I had tried every single one of the ubuntu versions,but had no hope) At last i am getting some normal fps in glxgears and hope i will get in other 3d programs as well!ACTUALLY JUST TRIED SOME GAMES OMFG OMFG SCREEN DOESNT FLICKER ANYMORE AFTER GAME ! THANK YOU THANK YOU AND THANK YOU :):):):):popcorn::popcorn:

---

