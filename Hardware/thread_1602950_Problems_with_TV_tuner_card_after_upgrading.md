---
title: "Problems with TV tuner card after upgrading"
date: 2010-10-22
forum: Hardware
---

### Post by selectedusername on 2010-10-22
Hi,

I have a Mystique DVB-C card which I use for my HTPC setup. The card has been working fine with MythTV for some months now. After the lastest kernel upgrade, however, the card stopped working!

dmesg | grep DVB
[   14.195117] DVB: registering new adapter (KNC1 DVB-C MK3)
[   15.192057] DVB: TDA10023(-1): tda10023_writereg, writereg error (reg == 0x00, val == 0x33, ret == -5)
[   15.304038] DVB: TDA10023(-1): tda10023_readreg: readreg error (reg == 0x1a, ret == -5)

What does this error mean and how do I fix it??

Thanks for any help in advance

---

