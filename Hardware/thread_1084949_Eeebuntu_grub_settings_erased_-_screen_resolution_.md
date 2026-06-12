---
title: "Eeebuntu grub settings erased - screen resolution doesn't work"
date: 2009-03-02
forum: Hardware
---

### Post by Qwertman on 2009-03-02
I need some help here. I'm fairly new to Linux, although I'm definitely getting the hang of fixing my problems. This one, however, has me stumped.

I recently tried installing webconverger to a second partition of my EeePC 1000...

Drive 1:
  7.5gb [ / for Eeebuntu and MBR and GRUB location ]
  .5gb [ empty ]<- This is where I put Webconverger
Drive 2:
  31.5gb [ /home for Eeebuntu ]
  .5 [ Swap area ]

...Turns out webconverger doesn't work as well installed, so I deleted the partition. Oops! When I installed webconverger it put it's own copy of GRUB on its partition and set the MBR to read from there. I got GRUB error 15 after trying to reboot from there. Ok, I can fix that. After Super Grub Disk failed to do the job for some reason, I booted Eeebuntu Base live cd from my flash drive and entered the following into terminal:

```
sudo grub
> root (hd0,0)
> setup (hd0)
> exit
```

Okay, reboot. Now I can boot into Eeebuntu, but the boot takes noticably longer (when it's spilling loading messages on the screen and [OK]'s, there are some items that take a while that I don't even remember seeing before). My biggest problem: My screen resolution is stuck at 800x600 and the monitor is labeled unknown. Also compiz effects are not working.

It seems to me that some graphical driver is not loading, probably because Eeebuntu needs some boot parameters to be set and restoring GRUB from the live CD did not use those parameters. I need to know how to fix this. Reinstalling is not an option for me because I REALLLLLLLY don't want to do that, and it would be useful to know how to fix this if others come up with the problem in the future.

---

