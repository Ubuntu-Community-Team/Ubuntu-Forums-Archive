---
title: "Wubi : can I install 9.04 and keep my 8.10 ?"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by JohanSamyn on 2009-05-21
Hi folks !
I have a nicely working 8.10 Wubi install on my laptop. Would like to try the new 9.04. But want to keep the 'old' 8.10 too. So, is it possible to have 2 Wubi installs next to each other ?
I think the issues are :
1) Is it possible to have Wubi install the distro in a folder instead of in the root of the C-disk ? (If not, my 8.10, installed automaticaly in C:\ubuntu, could be overwritten, unless I can force wubi to install in another folder then C:\ubuntu.)
2) Is it possible to make Wubi use a different name for the 2 files it writes on the Windows disk for use by grub ? (Now I see "wubildr" and "wubildr.mbr". I would like to be able to name the new ones f.i. "wubildr_9.04" and "wubildr_9.04.mbr".)
Can anybody help me on this please ?

---

### Post by madmaxou on 2009-05-22
what i did was burning an iso of jaunty and than just install (you have to make another partition).

---

### Post by JohanSamyn on 2009-05-22
Thanks for the reply Madmaxou.
But, you see, that's the point. I do not want to start fiddling with partitions. That's why I like the Wubi-way so much. Easy install, no fuzz. I know I may be asking for something a bit exotic. But if I don't ask, I won't ever know.
Btw: Did you end up having a "triple"-boot (win + ubuntu-earlier-than-9.04 + 9.04) ?

---

### Post by latefee on 2009-06-17
I have the same question, as I somehow ruined my current Wubi install by installing software with the wrong dependencies.  Anyway, I'd like to install a parallel Wubi instance next to my current install, then mount and transfer my files from the old to the new Ubuntu install.  Does anyone know if this is possible? Thanks in advance...

---

