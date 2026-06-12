---
title: "Installation on RAID fails as Raid not recognized"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by S_e_P_p on 2009-05-26
Hello All,

I`m trying to install Ubuntu 9.04. I have two 500GB Samsung in RAID 0. So it gives 1000 GB. If I try to install Ubuntu it sees only two hard drives with each 500GB, so it doesen`t recognize the raid.

A other strange thing which I recognized is that after I try to install ubuntu I have to shut down the PC complete. Otherwise the RAID isn`t correctly setup from the raid driver menu in BIOS.
(Which means after the pc starts there comes usually a screen which loads the raid. This says that the raid couldn`t be loaded)

But this problem is only after failure of linux installation.


My System:
Processor: Intel(r) Core(tm) 2 Duo/65nm E/X6850  Stepping:G-0
Chipset: Intel P31/P35
Mainboard: Gigabyte Technology Co., Ltd. P35-DS4

JMB36X PCIe-to-SATA-300/IDE RAID Controller, Giga-Byte Technology

Two 500GB SAMSUNG HD501LJ

Thanks for your help in advance.

Greets SePp

---

### Post by S_e_P_p on 2009-05-27
bump ... :p

---

### Post by ronparent on 2009-05-27
You should read the following and follow the instructions therein carefully:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I haven't confirmed that this howto is adequate to get a raid0 up and running with 9.04, but following it shoud be nondestructive and not render the array broken by raid bios!

Be aware that the ubuntu install doesn't, in my opinion, deal adequately with installing to raid in a typical so called fakeraid setup. It's possible, but, overly complex. Worse, it invites the unwary to destroy whatever is already loaded to their entire raid0 array. It is good that you were astute enough to realize that something was not right! Congrats.

---

