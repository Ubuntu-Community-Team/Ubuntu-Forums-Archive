---
title: "Trouble with Unity, AMD 7750 and proprietary drivers"
date: 2014-03-04
forum: Hardware
---

### Post by micelus on 2014-03-04
Hi folks,

recently I bought a new graphics card (Sapphire HD 7750) and I've got the weirdest problems tagging along with it. Even though I like opensource drivers and they are ok to just browse the web etc, since I bought dozens of games for Linux via Steam, I really need proprietary drivers. Those supplied as fglrx and fglrx-updates only crash my system in a way, that it boots directly into low graphics mode, which instantly freezes. When that happens, I cannot even get to the tty to try to fix it. So I downloaded BETA drivers from AMD website, built it, installed it and it worked... until I turned off the computer. After doing that, I cant login to any user but the Guest account - no black screen (from what I gathered, common problem), it just jumps back to lightdm. Through tty I installed gnome-shell, started Xserver and replaced the window manager with it and it works, so I guess, that the problem touches Unity only. Personally I would be able to grind my teeth and use pretty much anything, but my elder parents use the desktop while I am away and they fell in love with Unity. Since I don't want to reinstall opensource drivers everytime that I leave for a few days (every week), could you advice me on how to fix it?

Thanks a lot

---

