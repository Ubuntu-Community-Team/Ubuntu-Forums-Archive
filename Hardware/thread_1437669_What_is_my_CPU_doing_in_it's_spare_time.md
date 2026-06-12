---
title: "What is my CPU doing in it's spare time?"
date: 2010-03-24
forum: Hardware
---

### Post by johnuk on 2010-03-24
I've been experiencing some jumpyness with videos and such, so had a look at system monitor while I purposefully tried to recreate the jumps.

The results say my CPU can't cope, not the RAM.

But more interesting to me is that I tried closing everything and taking my hand off the mouse for a minute and my CPU levelled out and idled at around 20%.

It's not a problem (I hope), I'm just curious to know what it's up to in it's spare time. It's not like ram, where it's holding the OS and aps, I thought it would drop closer to 0%. Refreshing the RAM? I'm happy to admit I'm not sure.

Thanks for reading!
John

---

### Post by 3rdalbum on 2010-03-24
Your CPU should be idling at 1-2%, not 20%. You've got a program running that is eating up CPU power; kill it.

If Xorg appears to be eating up CPU power then you need to install a graphics card driver.

---

### Post by johnuk on 2010-03-24
Thanks for the reply.

Reset, started only sys monitor, let it sit for a few minutes and it's now at 15%. I haven't added anything to the boot of the GUI, it's still as it was from a fresh install.

Interesting you mentioned the video drivers, since I have video streams freeze for a few seconds every few minutes, but the audio continues.

Checked the drivers and I have NVIDIA's proprietary set installed.

---

