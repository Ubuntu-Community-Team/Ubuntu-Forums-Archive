---
title: "Can't get same screen resolution as live session after install"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by bluelamp999 on 2009-10-31
Hi all,

When I run a live CD session for Jaunty (and Karmic) I can select the correct native resolution for both my laptop screen (1920 x1200) and my attached monitor (1280 x 1024).

I can also enable compositing in Metacity and everything works fine...

I run my displays in 'big screen' mode.

However, after installing Jaunty I'm unable to set the same resolution for my laptop display - the max available is 1600 x 1024.

Can anyone explain why this might be and what I might do to fix it?

My graphics card is an ATI Mobility Radeon X300. I'm not using any proprietary drivers.

Thanks for any help...

---

### Post by lemming465 on 2009-11-01
It sounds like a bug in the X server, actually.

If upgrading to Karmic is an option, it's possible that the ATI support may have improved and that it will get the installed resolution right too.  If the [ aging proprietary binary ATI driver]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") supports that chipset you might be able to switch to that.

---

### Post by bluelamp999 on 2009-11-01
Upgrading to Karmic (clean install) fixed the issue!

Thanks...

---

