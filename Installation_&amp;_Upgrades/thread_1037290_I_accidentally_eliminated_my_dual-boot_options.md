---
title: "I accidentally eliminated my dual-boot options"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by bubbagumper6 on 2009-01-11
So I have Vista and Ubuntu installed, and it was set up so it would come to that screen with like 4 different versions of Ubuntu and Vista, then automatically load Vista.  Well I was going to try and triple boot so I could play around with Windows 7.  It didn't work out (not so compatible with my computer) but in the process it messed something up with Ubuntu.  My computer still works fine, and the Ubuntu partition is still ok, but the OS selector is gone.  So I have no way to boot it :(

I downloaded EasyBCD to get rid of the remaining Windows 7 selection so if it's possible to fix it with that, then great.  But I would like to have both the regular Ubuntu option plus the MemTest option.

---

### Post by chex_m8 on 2009-01-11
you probably wrote over the MBR when you tried to install windows 7
get out your ubuntu live cd and boot to it, then at the terminal
sudo grub
grub> find /boot/grub/stage1  this will return something like (hd0,?)
grub> root (hd0,?)
grub> setup (hd0)
grub> quit

---

### Post by bubbagumper6 on 2009-01-11
mmkay I'll give it a shot, thanks

---

