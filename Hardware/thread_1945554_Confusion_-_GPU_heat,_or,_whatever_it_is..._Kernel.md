---
title: "Confusion - GPU heat, or, whatever it is... Kernel related?"
date: 2012-03-23
forum: Hardware
---

### Post by janisgeiger on 2012-03-23
Hey.

Well, I've been trying all days to figure out what's wrong.

I'm running Ubuntu 10.04 with a 2.6.32-38-generic kernel and everything is near to A+ related to fan, temperature, gpu.

Now, I'm currently also running a version of #! (CrunchBang) using Debian Squeeze with a 2.6.32-5-686 kernel, and the temperature coming out is just horrible! Even though the cpu is down to its lower end.
I've read here on the forums that other users using Ubuntu switching to a new Kernel (like from 10.04 to 11.10) had an increase in heat also, so I'm confused if this problem is related to the kernel.

The thing is: I've also been using AV Linux, which is, well, also based on Debian Squeeze, and has a 3.0.16 Kernel. And the problem with temperature is exactly the same.

So, my two questions are:
What is it that Ubuntu 10.04 has, that supremely controls the, I assume? GPU fans etc, as 
- It's not the CPU! - I can look at it here, it's down to 3 % !! - 
+ it's also not related to the graphics driver, I think, in my case the fglrx driver, as an install in either CrunchBang or AvLinux didn't affect anything,+, I already tried every other option (open source, proprietary)

Second, what could be wrong with the temperature in general? Is it the GPU, or how could I control it? I'm pretty pretty much very much inexperienced in temperature and system hardware in general.

what is it exatly that I could "learn" from Ubuntu 10.04 to maybe implement into debian or something similiar related to a newer kernel, that would stop down my exceeded heatage? At the moment, I'd be absolutely trapped not being able to use it!

Everything I could find was related how to clock down your CPU, but not GPU.  "rovclock" did not affect anything while trying to use it to scale down GPU... (didnt get any temperature either, but it seems to be a *bug*).

Does something more general exist, that would tell the whole system hardware not to exceed over a certain temperature?


Btw, I'm using an AMD Mobilty Radeon 3400.
Motherboard "seems to be" an AMD Turion X2 QL 62, Dual Processor, 2GhZ... but as I said, the CPU is working nicely.


Another thing, I can't control anything heat / temp related in my BIOS settings either ;)
already did an.... bios update . . . . .    .  to check if that would help. Sooooo.... Any suggestions?

Cheers.


PS: I'd already be glad, if there wouldn't seem to be a solution, if someone could explain to me all that tech stuff. heatage while being in a pre-OS environment like BIOS or grub2 is up to near-maximum too... seems to be the operating system does have its own tools of controlling the gpu or anything related to it? (read about the cpu not given any "HLT instruction idle loop" when being inside BIOS...pheew?)

---

