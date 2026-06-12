---
title: "Ubuntu works fine, XP won't load on dual boot (n00b)"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by Catminister on 2009-01-28
I'm beginning to get overwhelmed browsing all the helpful information, so I thought I'd post.

I have an AMD 64 processor, 512 MB memory, 160 GB hard drive.  I have the Windows XP Media Center Edition preinstalled, with SP3.  I have Intrepid Ibex loaded over Hardy Heron (using upgrade utility within Heron).

I've tried to set up a dual booting system.  I used the guided partition method.  Unsure of what space to allocated (see aforementioned overwhelmed with information), I did a 60/40 split, with 40 to XP and 60 to Ubuntu.

XP, however, won't load.  When I choose XP from the boot menu,I get a blank dark screen with the words "starting up . . ." and a blinking cursor.

And nothing happens.  No matter how long I let the cursor blink.

I'm not sure if it matters, but I can access some of my XP files through the file manager in Ubuntu.  Other files (such as Windows' "My Documents") don't show up.

I could spend a few weeks browsing the forums after work, but I'm starting to get battle fatigue.  I was hoping someone could help me out as to what the problem might be.

---

### Post by dstew on 2009-01-28
Boot into your Ubuntu system and post the result of the following commands:```
sudo fdisk -l
cat /boot/grub/menu.lst
```We will look at the results and try to help you to boot your Windows.

---

