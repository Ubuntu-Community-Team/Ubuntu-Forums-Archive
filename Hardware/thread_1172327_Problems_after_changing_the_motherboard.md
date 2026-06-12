---
title: "Problems after changing the motherboard"
date: 2009-05-28
forum: Hardware
---

### Post by xaviersmp on 2009-05-28
Hello.
One day my motherboard stopped working and, therefore, I decided to change it. Even though the new one is similar, my kubuntu did not load anymore. Then I thought that I would have to install it again, which is something that I find understandable since I have had to reinstall Windows too. In order to do that I have used the Kubuntu LiveCD but the problem is that it gets a similar error and it does not work. It starts saying that it cannot read anything and everything gets stopped, with RSEISUB as the only way I have found to get out of there. I have tried an old Knoppix disc too and I also get an error, a PANIC: Segmentation violation, and it gets frozen.

Does this mean that my new motherboard (ASRock P4i65GV) is completely incompatible with Linux? Or the LiveCDs actually read something nasty in the Linux partition of the HD and they cannot take the proper configuration or something like this?
Maybe I should try a newer Knoppix or another LiveCD distro that is better recognizing hardware, but I do not know anyone. Anyway, what I fear is that, even if I formate and delete everything in the Linux partitions of my HD (from Windows), I will be unable to install Kubuntu in there. Therefore, I would appreciate if somebody answered me about what I could do.

---

### Post by xaviersmp on 2009-05-31
The problem that I get when I try to load the Kubuntu LiveCD (without quiet splash) is the following: The screen gets filled with many errors like:

```

SQUASHFS error: sb_bread failed reading block 0xa7ad7
SQUASHFS error: Unable to read cache block [29ed5a31:1592]
SQUASHFS error: Unable to read directory block [29ed5a31:1592]
```

(with the boot-time in front of them) and then it says

```

init: rc-default main process (2829) terminated with status 127
```

and everything gets stopped. The only way to get out is RSEISUB.

---

