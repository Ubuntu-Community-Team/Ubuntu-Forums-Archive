---
title: "Getting my all my graphics cards all in a row, Cannot recognize mult GFX card"
date: 2013-03-05
forum: Hardware
---

### Post by SkeeterBum on 2013-03-05
So I recently formatted my HDD for fun while I was running windows (no it was not fun). So I decided to go back and try my hand at ubuntu again. I have used it before for about a year on a laptop and now want to use it on my new computer build.

My system is
MOBO: Evga Z77 FTW
CPU: Intel 3570K
GPU: Radeaon HD 5830 x4

I successfully made a Ubuntu bootable UCB, installed Ubuntu, stupidly made only a swap and / directory (now I can't upgrade), and finally got to the desktop.

After this I downloaded (via their site) the AMD linux 13.1 Catalyst Control Center. (it was a .run file). I then used a single graphics card and rebooted. It worked, the driver recognized the card (aticonfig --lsa). But when I would shutdown and add the other three cards, it seems the driver was not loaded and aticonfig could only find the first card.

How do I get these other cards recognized and all in a row with my duckies? :) 



In the end I am trying to install and recognize all of my GFX cards, then I would like to be able to download and install CGMiner which is the software I use for Bitcoin mining.

---

