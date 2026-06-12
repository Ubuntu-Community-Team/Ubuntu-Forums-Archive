---
title: "[SOLVED] How to block ram allocation of a program to prevent system crash????"
date: 2008-11-04
forum: General Help
---

### Post by alberto ferreira on 2008-11-04
1-I don't have a swap partition, however there's a free partition in my hard-drive with 15 Gb. I already know how to format it but how can I use it in ubuntu?

2-I'm starting to use Blender and  I have 2Gb of RAM in my pc. Blender sometimes spikes it's Memory consumption and my pc runs out of memory and then crashes.
How can I limit the amount of memory allocated to a process to prevent this from hapenning?

---

### Post by sdennie on 2008-11-04
The command to limit memory usage is ulimit.  To see your user limits type:

```

ulimit -a

```

To limit your processes to, for example, 1.5G I think you can put the following in ~/.bashrc:

```

ulimit -m 1500000

```

I think that will cause blender (but not the whole computer) to crash if if goes over 1.5GB of RAM.

Also, if you were using swap, I think that Blender exhausting all your RAM (and even swap) would just cause Blender to crash and not the whole machine.  This link looks like it should be able to walk you through the process of adding swap: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Edit:
If I'm not mistaken, ulimit is per-shell so, you'd have to logout and log back in before the ulimit changes would show up in applications run from the Applications menu.

---

