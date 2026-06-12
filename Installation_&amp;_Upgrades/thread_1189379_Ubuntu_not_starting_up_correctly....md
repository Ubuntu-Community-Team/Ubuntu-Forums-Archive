---
title: "Ubuntu not starting up correctly...?"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by Tiger Fanfare on 2009-06-16
Hi.
When I turn on my laptop it gives me the choice to select either "Ubuntu" or "Microsoft Windows XP Home Edition" to run, when I pick "Ubuntu", it shoots up this right away:
> GRUB4DOS 0.4.4 2009-04-21, Memory: 639k / 1010M, MenuEnd: 0x43516
[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command competitions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exits. ]
grub>

Which I find rather odd, for before installing the "Ubuntu" OS, all the proper requirements were met.

Just curious how to fix it, it feels awful odd not being on a laptop, as I am on a PC right at this moment. 

Selecting "Microsoft Windows XP Home Edition" spits up an error, but this is not the area to discuss that. :).

Cheers!
Tiger Fanfare

---

### Post by merlinus on 2009-06-16
Seems as though there is a problem with grub, which is the bootloader.

If you can run from the live cd, open a terminal and post output of:

```

sudo fdisk -l

```

You also might try supergrub.

---

