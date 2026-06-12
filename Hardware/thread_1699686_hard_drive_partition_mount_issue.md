---
title: "hard drive partition mount issue"
date: 2011-03-04
forum: Hardware
---

### Post by m.dr on 2011-03-04
I am in a situation.

I moved the IDE drive I had on channel 0 / primary to channel 1 / secondary.

So now when I boot into Ubuntu (10.10) it does not find the partition mount point /space and swap I had on that drive.

What is the best way to remount the partitions /space and swap - permanently (meaning it will be there when I reboot). I understand I have to make some changes to /etc/fstab but unsure exactly what.

If someone could point me to a link on how to do this safely and correctly - would really appreciate it.

Also what happens to my previous /space mount that I still see - but with nothing in it.

Thanks for your help.

---

### Post by Bucky Ball on 2011-03-04
Have you changed the drive to secondary with the little switching pin on the back of the drive?

You will need to find out what the partitions are now recognised as. sda*? Identify the IDE.

---

### Post by m.dr on 2011-03-04
I have both the drives set as Cable Select. So that should be fine correct?

Or is it better to run them as Primary / Secondary?

Thanks.

---

### Post by Bucky Ball on 2011-03-05
I would try swapping the jumper, yes.

---

### Post by dandnsmith on 2011-03-06
> **m.dr said:**
> I have both the drives set as Cable Select. So that should be fine correct?
Or is it better to run them as Primary / Secondary?

Either is OK, provided it works with your hardware. Sometimes there is an issue because of the cable or the particular drives.

Find out what hard disk(s) is/are being seen by using *sudo fdisk -l* (that last is a lower case ell, not a one). That will list all the partitions on all the drives.
Then you can edit the /etc/fstab to reflect the new position.

HTH

---

### Post by oldfred on 2011-03-06
If using cable select you have to have the newer 80 conductor cable. If using the older 40 conductor cable you have to jumper master or slave. Some drives even require a jumper master with slave.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by Bucky Ball on 2011-03-06
> **oldfred said:**
> If using cable select you have to have the newer 80 conductor cable. If using the older 40 conductor cable you have to jumper master or slave. Some drives even require a jumper master with slave.



+1. My point exactly. ;)

---

### Post by m.dr on 2011-03-22
Thanks to all for your help. Got this resolved finally.
Setting the jumpers to primary/secondary helped.

Sorry about not responding earlier.

---

