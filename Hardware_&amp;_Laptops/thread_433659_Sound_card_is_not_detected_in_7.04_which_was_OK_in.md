---
title: "Sound card is not detected in 7.04 which was OK in 6.10."
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by ravinsp on 2007-05-05
The sound card in my laptop was detected correctly in Ubuntu 6.10. But when when I installed Ubuntu 7.04, it is not detected. What's the problem here and how can I fix that?

My laptop is Samsung NP R40.

Thanks.
-RavinSP-

---

### Post by Swankyman on 2007-05-05
Hi

can you post the output of these commands entered into the terminal:

dmesg
lspci
lsmod

rich

---

### Post by ravinsp on 2007-05-06
Thanks swankyman,

Here are the 3 files for the outputs of the 3 commands in the archive.

---

### Post by Swankyman on 2007-05-06
hi,

this is an easy one I think, try this:

in a terminal type:

sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto

if this makes your sound work then put this:

options snd-hda-intel probe_mask=8 model=auto

at the end of this file using:

sudo gedit /etc/modprobe.d/alsa-base

Rich

p.s taken from here:

[http://ubuntuforums.org/showthread.php?t=415821&page=2](http://ubuntuforums.org/showthread.php?t=415821&page=2)

p.p.s lspci tells you what things are connected to your computer and in it was:

 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01) 

I just searched for that and found the above pages :D

---

### Post by ravinsp on 2007-05-06
Thanks man, it was a great help. Now sound works fine.

I wonder why 7.04 is somewhat problematic than 6.10 ? (Although 7.04 has many new good features)

Thanks
-RavinSP-

---

### Post by Swankyman on 2007-05-06
Yeah, I wonder too. But everything worked perfect for me :D

rich

---

