---
title: "ALIENWARE nvidia 6800 won't work, it did last weekend"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by nmz787 on 2008-01-25
01:00.0 VGA compatible controller: nVidia Corporation NV45 [GeForce 6800 GTO] (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation NV45 [GeForce 6800 GTO] (rev a2)

I have two dual output DVI cards, they worked last week, I can't remember if it was before or after I recompiled the kernel with the newest sources, I added in support for the AMD opeteron dual core 64 in the kernel, I don't know if this means it's running 64bit or 32bit just recognizing the cpu better.

now nvidia drivers won't load, and I don't have twinview or openGL support :(

is this a 64 bit thing? when I added the cpu type into the kernel is this what did it? It won't even work when I boot using the old kernel.

---

### Post by Mikecore on 2008-01-25
> **nmz787 said:**
> 01:00.0 VGA compatible controller: nVidia Corporation NV45 [GeForce 6800 GTO] (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation NV45 [GeForce 6800 GTO] (rev a2)

I have two dual output DVI cards, they worked last week, I can't remember if it was before or after I recompiled the kernel with the newest sources, I added in support for the AMD opeteron dual core 64 in the kernel, I don't know if this means it's running 64bit or 32bit just recognizing the cpu better.

now nvidia drivers won't load, and I don't have twinview or openGL support :(

is this a 64 bit thing? when I added the cpu type into the kernel is this what did it? It won't even work when I boot using the old kernel.

most likely you didn't build your kernel with support for the nvidia chipset " under video"
options in your kernel config file. you probably need to rebuild your kernel. Why do you feel the need to recompile your kernel in the first place. If you want to run 64bit Ubuntu already has a kernel that will do that. Unless you have a new piece of hardware your looking to get running and you know your kernel doesn't support it you really don't need to rebuild it ever. ( the Ubuntu team updates your kernels for you when it's needed )
( if your just trying to be leet and learn howto do it thats fine too. it looks like you probably made a mistake in your options. try again! good luck

---

