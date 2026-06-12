---
title: "Toshiba booting problem"
date: 2014-01-07
forum: Hardware
---

### Post by theo.langsnoer on 2014-01-07
My Toshiba Pro L300 has a huge problem with booting. It started after my swap from Ubuntu 11.10 to 12.04.3 LTS. When I turn it on, it starts booting but before any sign of Ubuntu shows up, the laptop switches off. After about 3 seconds it turns itself on again. Then the GRUB menu comes up. Here I press ENTER to boot into Ubuntu. Then, after a few seconds, the whole sequence starts again. Finally, after six to eight times, I can log in. Then, after 5 to 10 minutes, my screen gets messy and the computer freezes. I can then only force it to shut down and start again. Finally, after 20 to 30 minutes, the laptop stays on, although once it switches off after about 45 minutes.
Please, who can give me some advice?

---

### Post by Bashing-om on 2014-01-07
theo.langsnoer; Hello !

What pops to my mind is bios hands off to grub (Grand Unifies Bootloader) and grub or related files are corrupt.
Let's see what results if grub is (re-)installed:
Boot ubuntu and issue the Terminal command:
Careful here, I am going to "assume" that ubuntu is the sole operating system installed onto the 1st hard drive (sda) - no separate /boot partition . BE SURE !
```

sudo grub-install /dev/sda
sudo update-grub

```

If the problem continues, will consider (re)building the initial ram image.

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

