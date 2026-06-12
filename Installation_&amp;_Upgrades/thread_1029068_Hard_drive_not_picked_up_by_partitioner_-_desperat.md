---
title: "Hard drive not picked up by partitioner - desperate"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2009-01-03
Hi all, 

Have used this to wipe an old hard drive:

[http://www.dban.org/](http://www.dban.org/)

Very efficient, perhaps too efficient because now trying to install Xubuntu on a friend's old machine and not seeing the hard drive when getting to the partitioner during install.

Desperately need help on this one as am at a friend's place and can't spend the next week nutting it out. 

Tnx in advance ... :)

---

### Post by logos34 on 2009-01-03
What about gparted? (it's included on the ubuntu cd, not sure about xubuntu)

Sometimes gparted can see what ubiquity can't

I'drecheck the hard disk detect settings in the Bios...try auto, lba, chs, manual

---

### Post by Bucky Ball on 2009-01-03
Nope. Gparted sees nothing. This is odd. I'll check the bios. I needed to pop the battery to get access to the bios for some reason the owner and I couldn't figure, so ... who knows. Any other ideas?

What exactly should I change that too in the bios? I am currently trying LBA. Anyone???

---

### Post by MighMoS on 2009-01-03
If your BIOS doesn't pick up anything, you're going to have a hard time seeing it in Linux. Assuming it does, though, what are the outputs of ```
dmesg
``` and ```
ls /dev|grep -e "^[hs]d.*"
```

---

### Post by Partyboi2 on 2009-01-03
> **Bucky Ball said:**
> Nope. Gparted sees nothing. This is odd. I'll check the bios. I needed to pop the battery to get access to the bios for some reason the owner and I couldn't figure, so ... who knows. Any other ideas?

What exactly should I change that too in the bios? I am currently trying LBA. Anyone???
Try setting it to auto.

---

### Post by Bucky Ball on 2009-01-03
I have tried reformatting with the gparted live cd and just about to check the results now ... the gparted live cd did pick up the hard drive and tells me it has done the job. Let's just see ...

Thanks for all your replies ...

---

### Post by Bucky Ball on 2009-01-03
Okay, formatted with gparted and all fine. Try to install Xubuntu and Ubuntu ... doesn't to see the partitions! Chuck in the gparted live cd back in and there they are, just as I formatted them! This is confusing and now getting real desperate. Anyone?

Thanks again for your suggestions ... :)

---

### Post by wpshooter on 2009-01-03
My best "guess" is that it is time that you tried re-downloading and burning your Ubuntu ISO.  Make sure that you burn at 4X or less (if possible) and then make sure that the first thing that you do afterwards is to check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

If this does not work then try doing the downloading and burning from another computer.

Good luck.

P.S. - Why would you have to take the battery out of the machine in order to get into the BIOS.  Something is wrong there !!!  Is the BIOS on the machine at the latest and greatest version ?

---

### Post by Bucky Ball on 2009-01-03
Both disks are fine. Take note, I have tried a working (it is installed on my own desktop) Xubuntu disk and a working (installed on my laptop) Ubuntu cd already. :)

OP could access the BIOS with password but couldn't change any settings. The battery popping exercise worked a treat and got everything back to normal (we could access BIOS settings again to change boot order).

---

### Post by mc4man on 2009-01-04
If still not working I'd try a couple of things. (in bios, for the primary drive, the drive type set to auto

You mentioned partitioning the drive, maybe try deleting the partition(s), leaving just unallocated space.

Otherwise a drive utility disk may prove helpful, preferably drive manufacturer specific.

The ultimate boot disk could be one to ck. (follow links out for info before using any.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

