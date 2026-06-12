---
title: "Having Hardware issues with Rendering"
date: 2022-04-09
forum: Hardware
---

### Post by laughing-imp on 2022-04-09
First of all, my most honest apologies if i'm posting this on the wrong place of the Forum. I'm rather new to communities like this, and I'm a little desperate. If this has been posted on the wrong side of the forum, Please inform me.

I'm working on an animated short as a college project, and the rendering process is really taking a while, to the point that i'm having to leave it rendering over night what is a really simple project (no photorealism). After digging some info on the notebook's hardware, I realize that it's only using 1 processor at a time out of 8 (4 physical processors, but 8 logical ones), and It really shouldn't be doing that. I'm using Blender 3.0 to render my project, and both the program AND the notebook have Mutil Processor Rendering supported and (in theory) enabled by default.

My notebook is a Samsung model NP350XBE-XD1BR  , running Ubuntu 20.04.3  (64 bit). The CPU is an Intel(R) Core(TM) i5-8265U CPU @ 1.60GHz.

Why am i posting it here? Well, I have a theory that this laptop is rigged hardware wise to not run any operating system that's not Windows on it, and that this issue has to do with the laptop having some sort of Battery Saving measure. But I can't find any information about it or anyway to use all the processors for rendering. My renders should be at least 6 times faster than they currently are, but they're not.

Does anyone have a laptop of this model, or at least a similar Samsung one? Is this a hardware issue? Or a conflict with the Operating System?

---

### Post by TheFu on 2022-04-09
I have an Asus with a Core-i5 8250U.  Under battery, the performance drops and video performance using the onboard intel iGPU is never great. It is good enough to watch videos, but not good enough for video rendering or editing at 1080p resolutions.

Keep the system plugged in.
Check that all the power saving features are disabled.
BTW, you don't have 4CPUs.  You have 1 CPU, with 4 cores and hyperthreading may not be enabled due to known Intel security faults. If you are willing to allow security to take a back seat, there must be grub boot options which disable each of the known intel security issues which have been rolled out over the last 5 yrs as they were uncovered.  I don't know how to do this, but I care more about security than performance.
Google found this: [https://ubuntu.com/blog/meltdown-spectre-and-ubuntu-what-you-need-to-know](https://ubuntu.com/blog/meltdown-spectre-and-ubuntu-what-you-need-to-know)
and
[https://linuxreviews.org/HOWTO_make_Linux_run_blazing_fast_(again)_on_Intel_CPUs](https://linuxreviews.org/HOWTO_make_Linux_run_blazing_fast_(again)_on_Intel_CPUs)
There are many, many, many, other pages. I've tried none of them.

BTW, AMD has a few similar security issues, just not as many. I haven't disabled the fixes for those on my Ryzen systems either.

If you want to see if your tasks really are limited to 1 core, use **htop**.  I haven't noticed any difference in core utilization on multi-threaded tasks. All 4 cores are working.

---

