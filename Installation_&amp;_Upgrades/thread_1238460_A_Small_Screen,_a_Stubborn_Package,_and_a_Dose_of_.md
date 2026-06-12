---
title: "A Small Screen, a Stubborn Package, and a Dose of Stupidity"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by Atomic Fusion on 2009-08-12
So, I had a fresh install of Ubuntu. Because I wanted to try Kubuntu, I installed kubuntu-desktop (might this cause a problem?). I had a tiny screen resolution, 800x600, and I know I can get up to 2048x1536 (I have it in Windows). So question number 1, how do I get that resolution? I tried adding "Driver "r128"" in the xorg.conf (I have an Ati Rage 120). It didn't do anything. Then I discovered displayconfig-gtk. But, I have Jaunty, it's for Hardy. right? So, my next problem...

In retrospect, YES, this was stupid. displayconfig-gtk relies on guidance-backends, which relies on Pytho being less than 2.6. I have 2.6.2. Sooo... I dumped out guidance-backends, changed the dependencies to anything less than 2.7, recompressed, and installed. I got an error (Error: Failed to satisfy all dependencies (broken cache)). Now, it keeps telling me to fix the broken package, but it's too far gone to remove without reinstalling, but I can't reinstall, and I can't update because the dependencies are wrong. So...

How do I fix my resolution? And, how do I remove that package? Could I still get displayconfig-gtk, or is that impossible on Jaunty?

Thanks,
Stephen

---

### Post by stlsaint on 2009-08-12
1. so on your windows screen you have low res...thats prolly a driver or settings issues!
2.have you tried the livecd to repair broken packages?

---

### Post by Atomic Fusion on 2009-08-12
Sorry, my **Ubuntu** screen has low resolution (800x600), my Windows screen is huge (2048x1536).
How would I remove the package with the LiveCD? This is my first personal Linux install.

Thanks,
Stephen

---

### Post by Atomic Fusion on 2009-08-12
OK guys, I'm sorry about bumping this, but I am really getting desperate and have no idea what to do. I can't install ANYTHING through Synaptic or apt-get or any other way I know! Thus I cannot install an earlier version of Python to satisfy the dependencies.

Please help!
Stephen

---

