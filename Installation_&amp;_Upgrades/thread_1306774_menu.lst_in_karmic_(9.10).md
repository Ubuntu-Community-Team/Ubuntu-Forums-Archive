---
title: "menu.lst in karmic (9.10)?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by MyCherries on 2009-10-30
Hi, I just switched to Karmic yesterday, and now after I have done most of the reinstalling of things, finally decided to do the ol' "noapic" trick. This wouldn't be an issue if I could only find where the darn "menu.lst" is. I navigated to /boot/grub/ but only found grub-menu.lst, and it doesn't have the boot parameters I see when I edit the kernel when booting. So I'd like to know where the "menu.lst" is, and what it has changed to (if it has). 

Here is what grub-menu.lst looks like...
```
 # sample /boot/grub/menu.lst entry for memtest86
#
# This example assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

title  memtest86+ (serial console 115200)
root   (hd0,0)
kernel /boot/memtest86+.bin console=ttyS0,115200n8 
```

---

### Post by grandtoubab on 2009-10-30
Karmic uses Grub2
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by arpanaut on 2009-10-30
Depends on whether you did an upgrade or a fresh install...

They spread some fresh grease on the learning curve this time around:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
and 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

good luck

---

### Post by MyCherries on 2009-10-30
Ah, thank you for shedding some light onto this topic. I searched for some info on this earlier (albeit I searched only 3 things) but found nothing... Thanks again for pointing me in the right direction.

---

### Post by axel_2078 on 2009-10-30
To save others from searching:

/boot/grub/grub.cgf

---

### Post by wkulecz on 2009-10-30
> **axel_2078 said:**
> To save others from searching:

/boot/grub/grub.cgf

You are not supposed to edit this one.  Read the link posted above, it has instructions for reverting.

I don't see any "improvements" listed for grub2 that is worth all the broken systems I see already!

--wally.

---

### Post by arpanaut on 2009-10-30
> **wkulecz said:**
> You are not supposed to edit this one.  Read the link posted above, it has instructions for reverting.

I don't see any "improvements" listed for grub2 that is worth all the broken systems I see already!

--wally.

I'm not seeing any more "broken systems" from grub errors this release than previous releases, It's just new, the documentation is not complete, and the number of people giving help with a working knowledge and experience are few and far between.

The documentation pointed to is excellent and does take some time to absorb, but since Grub2 is the GNU standard now, if you are going to keep up with the growth of linux it's time to start learning the new system.

It's prety straight forward on fresh installs, limited multi boot scenarios, even for noobs. The complication comes from extreem multiboot systems chainloads and various distros, but that hasn't always been straight forward anyway.

Plus, they had to go this way with Karmic because the bugs need to be worked out before the 10.4 LTS release, which appears will not have the option to revert to grub legacy. 

My advice is go with the flow, learn Grub2 now so you don't get caught with your pants down the next time around...  2cents

P,S. once you get past the learning courve the capabilities, customization, and automation is awesome and is just going to get better. And yeah I'm still working my way up the learning curve, sometimes it's mindboggling work... such is life!

---

