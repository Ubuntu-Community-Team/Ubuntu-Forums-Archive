---
title: "Dual Graphics on HP Pavillon dv6"
date: 2012-02-06
forum: Hardware
---

### Post by asdinnie on 2012-02-06
Hi Folks

I am running Kubuntu 11.10 on a HP Pavilion dv6 (dv6-3203tx)
Its got the dual / hybrid graphics in it: Intel/ Radeon.
I have just upgraded the kernel to 3.0.0.15 using the Kubuntu repos.

My kernel tells me the VGA switcheroo is enabled (using grep)

My BIOS does not appear to have an option to change the default GPU. (BIOS version: Insyde F.29 - latest version).

When I look at the kernel log it does not appear to load the radeon modules, only the Intel modules, as graphics modules.  The Radeon is available as a sound card though.

WHAT I AM AFTER:
I just want the Radeon to be the main GPU as this laptop runs on the mains power all the time.  I am not fussed about the powersaving mode of the Intel unit.

Reading the Hybrid Graphics page on the Ubuntu Documentation ([https://help.ubuntu.com/community/HybridGraphics):](https://help.ubuntu.com/community/HybridGraphics):) it tells me how to switch to integrated graphics when the X server is next restarted.
i.e. echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch


Two questions please:

1.  Does this command still work for the 3.0 kernels (the documentation appears to be for the 2.6.* kernels) ?  Or is there a better way to do this with the 3.0.* kernels?

2.  If the X session / laptop hangs because its not supported, can I get back to a working system?  And, if so, how?

Many thanks

Andy

---

