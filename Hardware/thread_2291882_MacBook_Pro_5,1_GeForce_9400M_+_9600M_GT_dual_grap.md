---
title: "MacBook Pro 5,1 GeForce 9400M + 9600M GT dual graphics"
date: 2015-08-23
forum: Hardware
---

### Post by astralnysledz on 2015-08-23
I would like to ask for help regarding a most unusual case. I have an old MacBook Pro 5,1 15-inches from *circa* 2008, which sports an **integrated GeForce 9400M **graphics adapter and a **discrete GeForce 9600M GT **graphics adapter. I went through half of the Internet (figuratively) and could not find a single constructive answer to my inquiry. I am writing on Ubuntu forums explicitly, because only on Lubuntu did I manage to make the most progress with this laptop. Here the story goes then...

1. The nouveau driver fails partially, because it is trying to power both cards, while one (discrete) depends on the other (integrated) for driving the display. Hence, I can launch X only in nomodeset mode. Curiously, certain colors are 'glitched' - specific shades of blue display as brown and orange, while light shades of orange display as blue.

2. Nvidia proprietary drivers work and nvidia-settings manages both cards, though which one handles programs is not known. A quick test with an OpenGL-heavy program Pymol showed only the integrated graphics card. Also, it is not possible to shut down the discrete card to reduce power consumption and heat emission.

3. The prime package for Optimus cards does not work, because it was designed for Intel + Nvidia setups, not Nvidia + Nvidia.

4. Bumblebee fails entirely as it blacklists the nvidia kernel module in favor of loading it only for designated programs. Again, this works only for Intel + Nvidia laptops.

**My question - Is it at all possible to manage those cards individually and use the discrete card for specific tasks?**

---

