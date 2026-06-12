---
title: "Can I delete HP partitions without braking Windows?"
date: 2011-08-24
forum: Hardware
---

### Post by teHIngo on 2011-08-24
Hey guys,

I just got my brand new HP Elitebook 8560w and am really happy with it. Of course the first thing I wanted to do with it is get Ubuntu on it asap. Didn't quite work out, here's my problem.

The partitions HP_RECOVERY and HP_TOOLS are put at the end of the partition table by default. The larger partition with drive C: comes before these, which makes it impossible to install Ubuntu alongside this using Ubiquity. Therefore, the easiest option would be to just delete those partitions, as they seem pretty useless to me, being a 99% of time Ubuntu user. 

Does anyone have experience with deleting those partitions? Will it break my system?

Cheers,
Ingo

---

### Post by dave01945 on 2011-08-24
my hp had an option to make a set of recovery discs but all the recovery partition is a way to reinstall windows if you need to not sure about tools though mine didn't have that

also you can resize your windows partition to make space not sure if windows can do this but gparted on the ubuntu install disc can

---

### Post by coffeecat on 2011-08-24
> **teHIngo said:**
> Does anyone have experience with deleting those partitions? Will it break my system?

Some people do delete both partitions, **after** they have made a set of restore DVDs. You can do a restore from the recovery partition and you need the HP_TOOLS partitions to make the DVDs.

What I did was to make the DVD set and then delete the HP_TOOLS partition only. Then I shrank the C: partition using the Windows 7 Disk Management Utility. Then I used Gparted on the Ubuntu live CD to make an extended partition in the space freed by shrinking the C: partition and installed Ubuntu into logical partititions within the extended.

The space freed by deleting the HP_TOOLS is still there unused up at the end of the disk, but it's only a few megabytes so that's of little consequence.

---

### Post by teHIngo on 2011-08-25
That perfectly answers my question! Thanks a lot for your help, I appreciate it.

---

