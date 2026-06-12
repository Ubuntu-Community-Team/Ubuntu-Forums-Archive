---
title: "Sound dies after autoupdate"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by isecore on 2007-01-19
Hi guys!

I'm a Ubuntu newbie (somewhat) and recently decided to give it a more serious go. Now, I've used Linux off and on for the last 10+ years, however this has almost exclusively been serveroriented. This means that I'm very rusty when it comes to Linux-desktops.

My question is simple. I installed Ubuntu 6.10 just fine and had a lot of fun adding XGL/Compiz as well as discovering that the Nvidia-drivers were in the non-free repository. Very nice!

The installation/Live-CD found pretty much everything in my computer. Networking, SATA, the works. It even found my obscure bluetooth-dongle! woot!

It also found and installed my Soundblaster Audigy2 ZS without a hitch.

However, after performing an autoupdate no sound comes from my speakers. I've checked the volume, the kernelmodules and everything. No indication of any errors, but there's still no sound! I don't know much about how ALSA works (hell, the last time I ran Linux on a desktop I just compiled the drivers into the kernel!) so I would appreciate it whole-heartedly if someone could point me in the right direction.

Thanks!

---

### Post by shutterbc on 2007-01-20
I had the same problem on my D620.  It's an Intel HDA audio card, and everything worked fine until I did my first round of updates including upgrading the kernel.

What I found is that though I don't seem to have ALSA working properly anymore, OSS still works.  Is that the case for you as well?

---

