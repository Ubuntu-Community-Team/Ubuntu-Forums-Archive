---
title: "Best Graphics Card for XGL/AIGLX"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by ferose2 on 2006-08-31
Anyone know a good mobile graphics card that's best for XGL or AIGLX?

---

### Post by Dittohead on 2006-08-31
Anything Nvidia really. Especially a 6 series or up, 5 series will do to a degree (5200 might be pretty slow though), anything under 5 simply doesn't work. At least my Geforce 4 Go doesn't. The latest is the 7 series, which has a fully programmable gpu. Most of the newer Quadros (up to 3 years old) should work well too, however the only laptops that I know of that contain Quadros are Dell Latitudes, Precisions, BOXXs and maybe a couple of the AlienWare computers.

Stay away from Ati unless you enjoy headaches. They have hit or miss quality drivers...mostly miss. They support only a small subset of their current GPUs and don't release new drivers very often unlike nvidia.

I can't say too much in the way of Intel as I try to avoid any computer with built in video cards. They're generally poorly built, use system cpu/ram and don't have pixel shaders. The newest GMA950 cards may have pixel shaders (they support Apple's Core Image API which requires a video card that can run programmable shaders) though I honestly don't know.

Any other chips I really can't say much about as I honestly don't know.

I would recommend NVIDIA. The only catch is that Nvidia doesn't have open source drivers (more specifically GPL). The only open source drivers are the GPL drivers from Xorg, which don't support XGL or very many nvidia cards (or the myriad hardware and acceleration features). If you're dead set against using linked in drivers that are not fully GPL'd, you're better off without XGL at the moment. Otherwise my recommendation an NVIDIA.

---

### Post by ferose2 on 2006-08-31
Thanks! You saved me a lot of headaches I was almost about to get an ATI x1400, but I changed my mind.

---

### Post by Melcar on 2006-08-31
I'm running XGL on my 200M.  With all the options enabeled it does have some slowdown. I was rather surprised that it even ran.  A x1400 should do nicely.  Of course, an nvidia card would be marginally better simply because of better drivers.

---

### Post by reacocard on 2006-08-31
I run AIGLX/Compiz on my intel 915 graphics with no problems. But if you have the money, by all means, go for Nvidia.

---

### Post by krazyd on 2006-08-31
With their monthly release schedule, ATI's drivers are rapidly catching up to Nvidia IMO. It'll be interesting to see who gets support for AIGLX first.

---

