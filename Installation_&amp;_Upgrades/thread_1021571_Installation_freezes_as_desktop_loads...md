---
title: "Installation freezes as desktop loads.."
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by blockdude14 on 2008-12-25
Just installed the ubuntu 10.10 x64 on my pc, I installed it from the alternate CD like I was told, burned at 4x and had the CD checked by the MSDUM5 and once installed when desktop loads it freezes? Why does this happen I tried it couple times?

I am running:
Asus motherboard
Gefroce 7800GT OC
AMD Athlon 3800 2.01GHZ
1 GB RAM
Sony CD/DVD drive
some mouse
logitech keyboard and webcam
forgot what sound card..


Please help:confused:

---

### Post by Partyboi2 on 2008-12-25
Hi, Have you tried using some boot options like noapic nolapic ?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by blockdude14 on 2008-12-25
The tutorial is a little complicated for me.. Can u tell me how to set it up in simple words how to set this up or fix it?

---

### Post by Partyboi2 on 2008-12-25
When you boot and see something like "grub loading..." press ESC to get to the grub menu, then highlight the first line and press "e" then highlight the line starting with "kernel" and press "e" again then at the end of the line add 
```
noapic nolapic
``` then press "enter" then finally "b" to boot. If this works you will need to make it permanent as the above method will only work for one boot. to test if it will solve the problem.

---

