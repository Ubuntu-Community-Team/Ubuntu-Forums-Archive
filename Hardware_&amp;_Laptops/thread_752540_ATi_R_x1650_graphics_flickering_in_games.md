---
title: "ATi R x1650 graphics flickering in games"
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by disturbed_one on 2008-04-11
First of all, my system

CPU: AMD Athlon64 3500
GPU: Radeon x1650 256 MB
RAM: 1GB
Ubuntu 8.04 Hardy

I'm a fresh Linux user, and I have a habbit of playing games here and there. I downloaded Alien Arena and Nexuiz. On AA the screen flickers now and then, and performance is not really good. Nexuiz is even worse. The game runs at very low fps, and it's unplayable. Now considering I could play Crysis on Low-Med setting on my previous XP installation, without big performance hits, I think these games should run fine. I tried the newest drivers, trie envy, but nothing can solve the problem.
I've searched the froums, and googled a bit, but nothing comes up. Could someone point me to where is the problem. I suspect drivers, and lousy support for my card.

On a side note, I will contnue to use Ubuntu no matter what, but it would be great if I could sometimes play a (3D) game or two her and there.

Thanks in advance,
disturbed_one

---

### Post by mrtomservo on 2008-05-08
Hello!  I've been looking for answers too.  I'm running an x1650 too, and anything that runs opengl gives me the flickers as well.  I first noticed it in Google Earth.  I've found that you have to disable compiz to work around the bug.  I'm not sure if it's a fglrx bug, or a compiz bug, or what.  You can disable compiz by going to System, Preferences, and Appearance.  Then go to the tab for visual effects, and set it to none.  From my understanding there's a problem with how compiz and opengl programs interact.  I would say it's particular to ATI acceleration, as I have installed 8.04 on a few other pc's with nVidia cards that do not seem to have this problem. It's something that I hope gets resolved soon, but luckily it's fairly easy to remedy.

---

