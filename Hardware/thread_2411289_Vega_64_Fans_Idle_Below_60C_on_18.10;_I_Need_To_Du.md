---
title: "Vega 64 Fans Idle Below 60C on 18.10; I Need To Duplicate That On 18.04"
date: 2019-01-28
forum: Hardware
---

### Post by lostmoonofsaturn on 2019-01-28
The fans on my Vega 64 card are intended to be idle at GPU temperatures below 60C.

This happens using 18.10.  But, it does not happen using 18.04, where the card's fans are on constantly.

My assumption is that it's due to the newer kernel in 18.10.

However, if I install a newer mainline kernel on 18.04 the fans remain on at all times.

Is my assumption correct?  Is there special sauce in the 18.10 kernel that is not in the mainline kernels?

What I need is a way to keep the fans idle below 60C using the 18.04 kernel.

---

### Post by CatKiller on 2019-01-28
There's been a lot of development on the AMD graphics side of things. You could try enabling the Hardware Enablement stack to see if it gives you all you need.

---

### Post by lostmoonofsaturn on 2019-01-29
> **CatKiller said:**
> There's been a lot of development on the AMD graphics side of things. You could try enabling the Hardware Enablement stack to see if it gives you all you need.


The Hardware Enablement Stack won't be available until after 18.04.2 is released next month. 

Right now, anything running the shipping 18.04 kernel is not an option for me.

---

### Post by CatKiller on 2019-01-29
> **lostmoonofsaturn said:**
> The Hardware Enablement Stack won't be available until after 18.04.2 is released next month. 

Right now, anything running the shipping 18.04 kernel is not an option for me.

The release version of  the kernel was 4.15. The HWE version is 4.18 (I'm running it now).

HWE will also bring updates to the graphics stack, although I don't know if that's happened already for 18.04 or not.

It's just a fairly painless mid-point between running 18.04 and running a later version for that kind of thing. It's worth trying, since it might work and it's easy to revert if it doesn't.

If that doesn't work for you, you'll need to track down which change to which package provides the change in functionality you need and get that, and its dependencies, installed. It could be in the kernel, or it could be in the graphics driver, or in the combination: I use Nvidia cards, so I've only got passing knowledge of the work that's gone into the AMD side of things.

I believe people using AMD hardware often use the [oibaf]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers") repository for updates to the Mesa stack, but, again, I only have passing knowledge about that. There is also the [Ubuntu-X]("https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates") repository for things that are newer than release but less cutting-edge than oibaf.

---

### Post by lostmoonofsaturn on 2019-01-30
My issue is the HWE kernel has not yet been released yet, the equivalent and later mainline kernels do not turn the fans off, and I've been looking for several weeks for an explanation. Unfortunately, kernel changelogs usually do not specify the impact of a change. Using upgraded Mesa stacks from the various PPA's has had no impact on the fans.

4.18+ kernels on other distributions usually, but not always, idle the fans correctly. 

I have an equivalent video card I could swap in but I change distributions enough to make the proprietary driver an annoyance.

---

### Post by CatKiller on 2019-01-30
> **lostmoonofsaturn said:**
> My issue is the HWE kernel has not yet been released yet
It has been released. I'm using it now. It's 4.18.0-14. I have no idea why you'd think that it hasn't.

---

