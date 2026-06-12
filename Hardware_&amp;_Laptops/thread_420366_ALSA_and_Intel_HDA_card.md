---
title: "ALSA and Intel HDA card"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by arekquest on 2007-04-23
I have laptop ASUS with Intel HDA sound card.
I was using Edgy, everything worked fine( I fixed a no-headphones-sound problem there).
Today I upgraded to Feisty. Sound worked just fine, except there was no headphones sound. I tried to fix it with: [http://ubuntuforums.org/showthread.php?t=76307](http://ubuntuforums.org/showthread.php?t=76307) but I got errors during makeing realtek drivers.
Now I am getting 

alsamixer: function snd_ctl_open failed for default: No such device

I don't really have idea what can be wrong, thus what listings shold I post. Thanks for support.

been trying to figure what's up, and:

lsmod | grep snd

gives me nothing?


 modprobe snd-hda-intelWARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/pci/hda/snd-hda-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory

how to fix it?

---

### Post by chewjoel on 2007-05-17
I have problem with my Asus M2400N laptop with Intel Sound Card to work on Feisty instead.
No sound at all. :( 
How did you get it works with yours?

Here's the thread of my problem:
[http://ubuntuforums.org/showthread.php?t=441823](http://ubuntuforums.org/showthread.php?t=441823)

---

