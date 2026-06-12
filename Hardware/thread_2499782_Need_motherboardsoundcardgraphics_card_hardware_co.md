---
title: "Need motherboard/soundcard/graphics card hardware combo recommentations that support"
date: 2024-08-10
forum: Hardware
---

### Post by yellowstarredfield on 2024-08-10
"Need motherboard/soundcard/graphics card hardware combo recommentations that support and optimize Linux/Kubuntu."

I'm rather new to Linux, having used different flavors over the last several years, and I haven't been able to get Linux audio successfully installed on my MSi Z270A Pro motherboard with an ASUS Xonar DGX soundcard.  I'm currently using Linux Mint on one hd and I'm currrently running some other programs on a hd with Kubuntu 22.04 but the audio isn't working on it either.
The processors: 8 × Intel® Core&#8482; i7-7700K CPU @ 4.20GHz
Memory: 62.8 GiB of RAM
Graphics Processor: AMD Radeon RX 460 Graphics
Apparently, the onboard MSi audio doesn't support Linux so I disabled it and I'm using the ASUS Xonar DGX soundcard off of another desktop computer.  
I'm committed to switching over to Linux by the end of Fall so I'll have to find a motherboard/soundcard/graphics card hardware combo recommendations that will use my current cpu, ram, graphics, and soundcard.  
Very soon, I'll have to get the lastest motherboard of whichever manufacturer produces one capable of optimizing Kubuntu and Linux.
I'm also running UbuntuStudio on an old Dell 660 desktop and the audio is just fine.
Thank you very much.

---

### Post by him610 on 2024-08-10
> onboard MSi audio doesn't support Linux so I disabled it
How did you disable it?

After it is enabled, please post results of this command within code tags
```
inxi -SMCAxz

```

---

### Post by Yellow Pasque on 2024-08-11
I'm confused. Does the Xonar DGX work or not?
> I'll have to find a motherboard/soundcard/graphics card hardware combo recommendations that will use my current cpu, ram, graphics, and soundcard. 
That doesn't make any sense. Why would you rebuild the system with a new motherboard and all the same major components just because the sound isn't working? Wouldn't it be a lot cheaper/easier just to get another sound device?
Oh, and the onboard sound really should work. It's a Realtek ALC892 codec, and they're very common. I know I've had at least one motherboard with it, and sound worked there.

---

