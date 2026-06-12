---
title: "How to find out if a game is running on the discreet AMD GPU (using radeon driver)?"
date: 2017-04-10
forum: Hardware
---

### Post by ilikestuff on 2017-04-10
Hello there.

I have an HP Dv6 6165tx running Ubuntu 16.10.

This laptop has the following switchable GPU setup:
Intel HD 3000 (integrated GPU)
AMD Radeon HD 6770M (discreet GPU)

I want to find out if the game Rocket League runs using the AMD card, because i am getting very poor performance even at very low graphics settings.

The output of ```
lspci -vnn
``` reveals that the open source Radeon driver is being used for the AMD graphics card:

```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT] [1002:6740] (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: radeon
    Kernel modules: radeon
```

Is there any way i can find out which GPU does the game use?

More information about the system:
HP DV6 6165tx
Intel Core i7 2670QM
AMD Radeon 6770M
Ubuntu 16.10
Kernel: 4.8.0-46-genericAny help would be appreciated!

---

### Post by ilikestuff on 2017-04-10
I should have done a little more research before posting this.

I found this thread on reddit: [https://www.reddit.com/r/linux_gaming/comments/5m58l1/how_do_i_find_out_if_steam_is_using_my_graphics/](https://www.reddit.com/r/linux_gaming/comments/5m58l1/how_do_i_find_out_if_steam_is_using_my_graphics/)

If you have a set-up like mine, and you have DRI3 enabled, just use the launch option ```
DRI_PRIME=1 %command%
``` for each game. This will make sure that the game launches using the discreet AMD GPU.

---

