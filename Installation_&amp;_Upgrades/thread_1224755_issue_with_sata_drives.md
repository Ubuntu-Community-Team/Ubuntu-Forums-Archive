---
title: "issue with sata drives"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by northstar67 on 2009-07-27
hi all 
I am  a new convert to the Linux world.
I installed ubuntu 9.0.4 but not without a struggle.
At first I wanted to use my sata drives and the CD installed apparently well, but at reboot time it would stop at GRUB Loading . . . Stage 1.5 or something similar.
I then tried to install on an ide drive and all went fine.
If i attach the sata drive ubuntu does not load.
I edit the kernel entry by hitting Esc at boot up and added all-generic-ide at the end of the string, then press b and it boots with the sata drive attached. I can see its content and all.
I then edit the menu.lst file permanently, reboot and same story, it stops and does not load.
I am a beginner so I do not know any other tricks or boot parameters to try.
If anyone has a good suggestion i will try it.

---

