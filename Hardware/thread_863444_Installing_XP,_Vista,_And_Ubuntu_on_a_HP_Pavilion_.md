---
title: "Installing XP, Vista, And Ubuntu on a HP Pavilion dv6000 laptop"
date: 2008-07-18
forum: Hardware
---

### Post by DaF101 on 2008-07-18
Hello everyone
I have recently purchased a HP pavilion notebook

When I got it, it came with Windows Vista Home Premium, which is okay because it came with all of the drivers installed (Less work for me :D) But I want XP back on there. and I want my Linux on there as well.

I tryed to tripple boot the operating systems before and I did not have much succsess. 

I tryed to Install the factory Vista on the notebook first, then Install windows XP, then after that fix Vista's MBR so it will boot into vista, after I booted into vista, I installed easy BCD on there and added XP as an entry so that it should give me the option with XP and Vista when I go to boot in, but ontop of that, I havent had much succsess dual booting vista and Ubuntu alone as well with XP

If anyone knows a quide to it, or can explain how to do it to me in detail, it will be well appreciated.

Cheers,
DaF101

---

### Post by phidia on 2008-07-18
There's a guide [here]("http://www.swerdna.net.au/linhowtoboot1.html") on doing that both with the window's bootloader or with grub.

You should use the alternate install cd for ubuntu because that allows you to install grub to the root partition (install partition) and not your MBR.

---

