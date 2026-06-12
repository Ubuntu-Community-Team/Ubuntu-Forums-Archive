---
title: "dell latitude ppx graphics"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by alien53 on 2007-11-09
I have an old laptop (as per the title!) which worked very well with the live CD of version 7.10. Then I installed the o/s and the graphics is so bad it's unusable (about 600px, 56Hz).

The default grpahics driver that the Live CD used was apparently very good, and the full install, if it identifies the laptops graphics hardawre, makes things worse.

So how can I install 7.10 and stick with the graphics that the Live CD uses?

Please?

---

### Post by overdrank on 2007-11-10
> **alien53 said:**
> I have an old laptop (as per the title!) which worked very well with the live CD of version 7.10. Then I installed the o/s and the graphics is so bad it's unusable (about 600px, 56Hz).

The default grpahics driver that the Live CD used was apparently very good, and the full install, if it identifies the laptops graphics hardawre, makes things worse.

So how can I install 7.10 and stick with the graphics that the Live CD uses?

Please?

HI and welcome. You may try enter this command in the terminal 
```
sudo dpkg-reconfigure xserver-xorg
``` and answer the questions. Choose vesa as the driver and if you do not know the answer to the other questions then leave as default given. When choosing your resolutions use the spacebar to select them. Good luck! :KS

---

### Post by alien53 on 2007-11-12
Thanks very much. I also installed Ubuntu on a desktop and it's better than XP (!). I'm in danger of over-enthused off-topic rambling. Bye :)

---

