---
title: "Ideal CPU &amp; RAM for Linux gaming PC"
date: 2020-06-09
forum: Hardware
---

### Post by jcdenton1995 on 2020-06-09
Hello all,

I'm building my first PC and I'm just at the point of starting to look at specific components.

What would be the necessary level of CPU and amount of RAM for, as an example, running AAA titles in a full windows virtual machine - not WINE (this is the most demanding use case I can think I would need to prepare for)

I'd be prepared to go with a Ryzen 7 3800X and 32gb of DDR4 RAM as I'm pretty sure that would eat it, but also I'm not sure if that's total overkill and perhaps I could get away with something like a Ryzen 5 3600X and maybe a little less RAM?

Any info is appreciated!

---

### Post by CatKiller on 2020-06-09
> **jcdenton1995 said:**
> running AAA titles in a full windows virtual machine 

It's not a great solution. You need a whole extra (non-Nvidia) GPU for that. Many games that won't run in Wine - because of DRM or anti-cheat - won't run in a VM either.

> I'd be prepared to go with a Ryzen 7 3800X and 32gb of DDR4 RAM as I'm pretty sure that would eat it, but also I'm not sure if that's total overkill and perhaps I could get away with something like a Ryzen 5 3600X and maybe a little less RAM?

The general principle is that you'd look at the requirements of the software you want to run in the VM, add on a bit extra to account for VM overhead (which is generally small but non-zero), and then add on how much extra the host needs to run the other stuff you might be doing while the VM is running. That's how much machine you need. 

16 GB is really the minimum that you'd want for a new machine *anyway*, even if you're not using VMs. 32 GB is already a reasonable choice for a lot of gamers if they tend to do other stuff at the same time. When you're running the VM the RAM that it uses won't be available to the host.

---

### Post by jcdenton1995 on 2020-06-09
Thanks for the reply, yes I had forgotten about the dual GPU need when running a VM. Just an idea, If I had a CPU with integrated graphics and was powerful enough, as well a a discrete GPU, do you think that would work if the GPU was used for the VM? (I don't plan to do that as I don't think there are any Ryzen 5's or 7's that have integrated graphics, but I may be wrong)

To be honest I'm not enough of a gamer to justify buying a 2nd graphics card, I'd be happy enough with the Linux native games / ports and whatever I could run in WINE to be honest. If I was that bothered about compatibility and performance I'd just use windows, but I'm not. Maybe I'd buy a second, used GPU in a few years time or something.

Edit: Actually there is a Ryzen 5 3400G with integrated graphics and another 2nd gen Ryzen 5 who's name I can't remember.

---

### Post by CatKiller on 2020-06-09
> **jcdenton1995 said:**
> Thanks for the reply, yes I had forgotten about the dual GPU need when running a VM. Just an idea, If I had a CPU with integrated graphics and was powerful enough, as well a a discrete GPU, do you think that would work if the GPU was used for the VM? (I don't plan to do that as I don't think there are any Ryzen 5's or 7's that have integrated graphics, but I may be wrong) 

As you've already found, there are some Ryzens with integrated graphics - the ones with a G, called APUs. 

That is the way that some people do it; use the integrated graphics for the host and a dedicated GPU for the VM rather than having two dGPUs. You can do GPU passthrough with Nvidia GPUs, just not the consumer ones: it's a feature that's restricted to the Quadro line. I don't think AMD ones are restricted. You also need a motherboard that supports it. 

It's not VMs in general that need passthrough, but VMs for gaming. Games really want the GPU all to themselves. 

> To be honest I'm not enough of a gamer to justify buying a 2nd graphics card, I'd be happy enough with the Linux native games / ports and whatever I could run in WINE to be honest.

I *am* enough of a gamer to see it as worthwhile to put a lot of money into my gaming rig, and I don't use Windows or a VM. [Steam](https://store.steampowered.com/linux) and [Proton](https://www.protondb.com/) makes it a doddle to play games on Linux. Some don't work, but more than I'll ever have time to play do.

---

### Post by jcdenton1995 on 2020-06-09
> **CatKiller said:**
> As you've already found, there are some Ryzens with integrated graphics - the ones with a G, called APUs.


Its a shame that there aren't any higher end AMD APU's as I'd really like to have integrated graphics as a backup for in case my graphics card blows up (not literally of course) and for the VM scenario, as it seems like massive overkill to have a dedicated graphics card for the host, although I have just realised while writing this that maybe I could just buy a potato of a g-card for the host and use the main card for the VM?

Also I read somewhere that there are motherboards that have integrated graphics too, so maybe that's an option?

[QUOTE=CatKiller]Some don't work, but more than I'll ever have time to play do.[/QUOTE]


Exactly, and even if I did get through all the titles I want to play, by that time many more will likely be supported anyway.

---

