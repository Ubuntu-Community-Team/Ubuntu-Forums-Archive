---
title: "A few minor questions about 8.10"
date: 2008-10-30
forum: General Help
---

### Post by johnnyxxxcakes on 2008-10-30
I just upgraded tonight, and I'm very pleased with everything. I love the new updated software that I use very frequently, and I love the new DarkRoom theme.

Aside from that, I've noticed that a few things run a bit sluggish, but not sluggish as to where I'm extremely concerned. Things that run slow are the Compiz Cube, and just average scrolling through web pages with Firefox, or scrolling through Music or Picture folders in Nautilus, and flipping through windows using Windows *Super* Key + Tab.

Is this normal? My specs should be plenty enough:
-Intel Pentium Dual Core 1.60GHz
-2 GB DDR2 RAM
-384 MB of shared video memory

---

### Post by jpeddicord on 2008-10-30
> **johnnyxxxcakes said:**
> I just upgraded tonight, and I'm very pleased with everything. I love the new updated software that I use very frequently, and I love the new DarkRoom theme.

Aside from that, I've noticed that a few things run a bit sluggish, but not sluggish as to where I'm extremely concerned. Things that run slow are the Compiz Cube, and just average scrolling through web pages with Firefox, or scrolling through Music or Picture folders in Nautilus, and flipping through windows using Windows *Super* Key + Tab.

Is this normal? My specs should be plenty enough:
-Intel Pentium Dual Core 1.60GHz
-2 GB DDR2 RAM
-384 MB of shared video memory

For some reason I've noticed this every now and then. Best bet is to do a full reboot and the problem goes away. I'm not quite sure what triggers it, or if it is only relevant to my machine. My specs are very similar to yours.

---

### Post by pirattrev on 2008-10-30
my guess is that some aspect of the new release is causing certain things to have different gpu priority, so it tries to do some things more then others (or do at all), slowing down the cube and such other graphic stuffs.  Nothing you can really do about it, 'cept hope somebody happens to find the line of code and fix it in an update.

---

### Post by El Chupacabras on 2008-10-30
I'm downloading 8.10 as of now, but something similar happened to me with Hardy Heron. I am constantly battling against memory being swapped out. I read somewhere that it's due to Xorg with the nVidia blob driver.

I haven't bought more memory yet, so I just restart firefox and use *$ sudo swapoff; sudo swapon;* to clear the swap.

However, since your computer shares memory with the GPU, I think its safe to say that your system swaps out more often, especially with Compiz on. Have you tried [changing the swappiness]("http://kerneltrap.org/node/3000") to something lower than the default?  (use *$ cat /proc/sys/vm/swappiness* to see what it is currently set to)

> **pirattrev said:**
> my guess is that some aspect of the new release is causing certain things to have different gpu priority, so it tries to do some things more then others (or do at all), slowing down the cube and such other graphic stuffs.  Nothing you can really do about it, 'cept hope somebody happens to find the line of code and fix it in an update. 
Maybe they changed the default swappiness value?

---

### Post by kaibob on 2008-10-30
> **johnnyxxxcakes said:**
> Aside from that, I've noticed that a few things run a bit sluggish, but not sluggish as to where I'm extremely concerned. Things that run slow are the Compiz Cube, and just average scrolling through web pages with Firefox, or scrolling through Music or Picture folders in Nautilus, and flipping through windows using Windows *Super* Key + Tab.

I noticed the slow scrolling in Firefox with 8.10 even after all the normal tweaks. I tried a new Firefox profile and that didn't help either. Finally, I restored 8.05, and Firefox scrolling speed increased significantly.

---

### Post by johnnyxxxcakes on 2008-10-30
> **El Chupacabras said:**
> I'm downloading 8.10 as of now, but something similar happened to me with Hardy Heron. I am constantly battling against memory being swapped out. I read somewhere that it's due to Xorg with the nVidia blob driver.

It could be the swapping issue, which I'll have to read up on. I don't use an nVIDIA graphics card though. I believe I have an Intel Mobile Graphics Media Accelerator X3100 graphics card, but it could all be related to the same issue.

---

