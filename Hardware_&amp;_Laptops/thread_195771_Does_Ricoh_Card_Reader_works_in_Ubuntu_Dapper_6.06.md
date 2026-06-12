---
title: "Does Ricoh Card Reader works in Ubuntu Dapper 6.06?"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by CAFH on 2006-06-13
Hello,

I am working with ubuntu for a quite time in my laptop, everything works great except my built-in card reader. Does the new version of Ubuntu solve this problem?

The last time i query for a solution, the only way was compiling the kernel.

Thanks for your reply,
CAFH

---

### Post by DavidFong on 2006-06-15
Dear CAFH,

The good news is that if you are referring to the SD/MMC card reader, I was delighted to find that Xubuntu 6.0.6 and the default kernel 2.6.15 does automatically recognise cards in the SD slot.

lspci on my machine shows...

0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSO Host Adapter (rev 13)

and /proc/partitions shows 

254 0 249856 mmcblk0      (major minor #blocks name)
254 1 249805 mmcblk0p1

Unfortunately, the compact flash card no longer works. lspci on my machine (a Sharp Murasama CV50) shows...

CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)

...and the problem is that pcmcia or ide keeps on trying to access hdf (which does not exist, the compact flash should only have hde and hde1), resulting in lost interrupts and an inability to access hde1.

I have not figured out how to solve that problem yet.

Cheerio, David.

---

### Post by jjcv on 2006-06-17
Works fine on my Inspiron 6400.

---

### Post by ponkarthik on 2006-06-17
Hi it works fine with my Dell Inspiron 6400 too for SD cards  - out of the box. But when when I insert my pro duo card from my mobile thro its adapter it doesnt recognise. but it works with XP. Any solutions ?

Thanks

Karthik

---

