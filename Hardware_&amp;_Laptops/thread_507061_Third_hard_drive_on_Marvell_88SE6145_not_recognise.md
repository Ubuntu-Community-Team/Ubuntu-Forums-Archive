---
title: "Third hard drive on Marvell 88SE6145 not recognised"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by Gimli on 2007-07-22
Hi all, 
I have the Asus P5W64 WS motherboard. It has ICH7R serial connectors which which is connected to my operating system disks and all works fine. 

The second SATA controller is a Marvell 88SE6145 with three connectors. I connected 3 seagate disks to it and only the first two comes up. I am convinced this is a driver issue as WinXP picks up all three.

In hardware information, the node under which the two scsi devices are listed shows 
"Unknown (0x6145)"

When I google for the issue I get to this link but I am to much of a noob to make anything of it. [http://ussg.iu.edu/hypermail/linux/kernel/0707.1/1110.html](http://ussg.iu.edu/hypermail/linux/kernel/0707.1/1110.html)

Can anybody help me fix the problem?

Help much appreciated.

---

### Post by Gimli on 2007-07-23
Anybody with ideas? Similar issues?

---

### Post by Gimli on 2007-07-24
Nothing hey?

---

### Post by racmar on 2007-08-02
I am having the exact same problem with Asus P5WDG2 WS Pro motherboards.  These boards have the Marvell 88se6145 chip, with 3 internal sata and 1 esata.  We have three of these boards and the same symptoms:  The first two drives are seen, but both of the other two never appear.  If I change the bios to enable the Marvell Raid Bios, I see all four drives on the screen in the Marvell config.  However, Feisty cannot see any of the drives not even the first two.  I'm sure it's a driver issue as I see an error message just after loading the pata_marvell driver.   
The error is:
```
ATA: abnormal status 0x7F on port ______
```

---

### Post by amorangi on 2008-02-13
I have this problem too - was there ever a resolution to this?

---

### Post by pixelbrei on 2008-07-01
Finally someone with the same problem.
I have had this for some time now, with debian and gentoo.
I wanted to switch to (k)ubuntu, because it worked fine with the fresh 8.04 install (amd64).
I could access all 6 hard disks without problems.
Now i reinstalled from the alternate cd to get encrypted lvm, and the problem is back.

I have kernel 2.6.24-19-generic running now (which has the problem).
the old kubuntu install was 2.6.24-1-amd64.

Is there a way to downgrade the Kernel to the one that worked?
Or to undo whatever patch it was to remove the working status again?

EDIT:
I think i broke it down to an initrd problem, because with the alternate-installer-cd
i got all 6 hard disks recognized during install (2.6.24-16-generic).
When i boot the encrypted system with the same kernel, it misses the 6th disk.

any idea how this may be fixed? both initrds use the pata_marvell module, no sata_mv involved.

---

