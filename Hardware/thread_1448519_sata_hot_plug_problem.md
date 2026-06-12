---
title: "sata hot plug problem"
date: 2010-04-06
forum: Hardware
---

### Post by pablo79 on 2010-04-06
Dear all, I've installed my mythbuntu 9.10 on a sata hd, I bought 3 others wd20ears to create (successfully) a raid 5 with mdadm on my gigabyte ga-ma790gp-ds4h based on ati 790gx. My bios sata ports setup is on ahci for all 6 sata ports so I expected that when I tested to hot-swap and hot-plug 1 hd the system starts to rebuild the raid but it didn't happen. It starts to rebuild only after a rebbot. The problem is linked to the fact the drive is not presents in the system until the rebbot due to, I think, a missing ahci configuration.
I've read some information about ahci and it seems that my board is completely supported by ahci module but it is not loaded in my system (lsmod | grep ahci doesn't show anything). My kernel is 2.6.31-20-generic-pae.
What I can do?

Thank you for your attention and help

---

### Post by pablo79 on 2010-04-07
](*,) I'm so stupid!! 
I tried to restart from the beginning:
the hot-swap/hot-plug work correctly, in fact when I replug the hd it appears again in the dev but as a new drive, i.e. I had /dev/sda1, /dev/sdb1, ... after the test /dev/sdb1 disappered and became /dev/sde1.

The problem is how to make the system assign the previous device id when it is plugged/unplugged to allow mdadm to rebuild immediately the array when a disk is replaced.

---

### Post by ottopaul on 2010-04-09
Can you confirm that the WD20EARS is working well on ubuntu 9.10? I have installed one as a single diskm but I have problems when transferring large quantities of data. [More about my problem here]("http://ubuntuforums.org/showthread.php?t=1448509").

---

