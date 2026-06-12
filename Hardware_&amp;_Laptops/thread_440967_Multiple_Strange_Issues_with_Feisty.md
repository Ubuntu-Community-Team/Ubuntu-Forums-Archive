---
title: "Multiple Strange Issues with Feisty"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by rjray on 2007-05-12
A laptop (Hewlett-Packard Pavilion zd7000) I have that recently suffered a complete HD crash, I freshly installed Feisty on. Before the crash, it had Dapper.

Interestingly, some things work better with Feisty-- CPU scaling had a broader range, the restricted Nvidia driver works much better.

But suspending is badly broken for me. And recently, CPU scaling has stopped working (it stays at the maximum speed whether the governor is "performance", "userspace", "ondemand", etc.). The lack of suspend is the worst... half the utility of having a laptop is being able to suspend it, go somewhere else, and pick up where you left off.

What happens is, after a fresh boot, the first time I suspend (whether to disk or RAM), it suspends fine. And it resumes fine (I love that suspend-to-RAM <almost> works). But the second time, it hangs during the suspend procedure. Blank screen, no disk activity. This happens whether I go to disk or RAM, or whether I did one first then the other. I tried installing uswsusp, but "s2disk" didn't suspend right even the first time with it installed. I tried installed Trevino's Feisty kernels with Software Suspend 2 patched in, but then I lost the ability to use the restricted drivers (and I have a wide-screen that doesn't get the resolution right under the "nv" server module, only under the "nvidia" driver).

I have no idea why CPU scaling went weird on me. It had been working fine. Ever since I re-installed the stock Feisty kernels to replace the Trevino ones, it's been stuck at the max speed. Of the two, I am *much* more worried about being able to suspend and resume. Losing my desktop every second session is getting old, fast. I hope to avoid a complete re-install, because I do a ton of development on this machine. After I installed from the LiveCD, it takes forever to go through Synaptic and install all the dev-related tools and packages I need that aren't installed by default. (This is my only gripe with Ubuntu... with Fedora, I could check a box that said "install everything", then go back and remove what I didn't want, which was a much shorter list to deal with. Still, it's worth enduring that inconvenience for the ways in which Ubuntu works better on my hardware.)

Randy

---

