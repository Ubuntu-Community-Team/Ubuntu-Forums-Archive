---
title: "2 Drives, 2 OSes"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by Grafixx01 on 2009-05-27
Hello all,

I'm new here, but it's great to be here. I'm trying to move completely away from Microsoft, at home at least since work sees Microsoft as like a GOD and they do not wrong, however, I've loaded Microsoft XP Pro and Ubuntu 8.10 on my OQO UMPC, which works great as dual boot.

However, my issue is this, I've loaded MS XP Pro on an 80gb drive and Ubuntu 9.04 on a 120gb drive on my Dell Desktop. Now I'm trying to put the two drives in, on different SATA cables but want to make the Ubunut drive first and the Microsoft drive second. But I want to be able to have a dualboot machine, giving the option of which drive / OS I want to run. Is it possible? What's the easiest way? 

I'm figuring to somewhat follow another post I was reading about making XP Pro the primary booting OS, but from what I've read, most people do it on a single drive not separate drives. Any ideas?

Thanks in advance,

Bryan

---

### Post by presence1960 on 2009-05-27
I originally had my dual boot set up on 2 different drives. Ubuntu on a 250GB SATA and Windows on a 160GB IDE. It was a two step process for me. I had to go into BIOS and set the drive with Ubuntu as first boot in the boot order. That got Ubuntu booting but not Windows. I had to edit my Windows entry in menu.lst file to look like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify    (hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

Of course the rootnoverify (hd1,0) needs to be changed to what disk & partition your Windows OS is. If not sure of this run in terminal > sudo fdisk -l. GRUB counts the first disk as 0 and the first partition on a disk as 0. The map lines will trick the egotistical Windows OS that it is first in the boot order or else it will not boot for you.

If GRUB menu does not come up when you boot you will have to boot into the live CD and restore GRUB from a terminal.

This is what worked for me.

---

### Post by Grafixx01 on 2009-05-27
Cool, thanks! I'll give it a whirl!

---

