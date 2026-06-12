---
title: "Install on eeepc 901 with multiple ssd drives"
date: 2012-08-20
forum: Hardware
---

### Post by El-ahrairah on 2012-08-20
Hi everybody,

I'm posting this question here 'cause it seemed the best choice, I hope it is the correct one.

I wanted to ask this: I have an eeePC 901, which has two ssd drives, the main one is 4GB and the second one is 16GB, is there a way to install ubuntu 12.04 on it using the two drives as if it was a single 20GB drive?

If it is possible, could you please explain me the correct procedure to follow?

Thanks in advance.

---

### Post by El-ahrairah on 2012-08-22
No one can help me with this problem? Is there no way to do it?

---

### Post by Ubun2to on 2012-08-23
RAID could help you, but with different drive sizes, probably not. There are plenty of different types of RAID arrays.
RAID 0:
RAID 0 splits files into 2 parts. Lets refer to them as parts A and B. Drive 1 gets part A, and drive 2 gets part B.
But, if you have different sizes, this could happen:
```
File: Drive 1: Drive 2:
1        A        B
2        A        B
3        A        B
4        A        B
5   out of space  B
```
Consider this: Ubuntu takes up 5 GB of space.
If it is split across 2 drives, you are using 2.5 GB (5/2=2.5) on each drive.
If drive 1 has 4 GB of space, that means you have 1.5 GB (4-2.5=1.5) left to store. The amount of space you can safely use is 3 GB (1.5*2=3). If you use more than 3 GB of space for things like updates, programs, and documents, etc., you have no more room.
But, this is where it gets tricky. Manufacturers claims of space-well, the hard drive usually only holds 93% of the claimed value (if it is listed in GB, it is 93%-listed in MB and KB, the actual space % is higher).
So, lets do some math!
_x_=_93 _
4=100
Lets break down the equation.
x/4-x is the actual capacity, and 4 is the claimed capacity.
93/100-93% is the percentage of the claimed space that you actually get, and 100% is the total capacity that you would have IF they were truthful.
So, according to cross multiplication...
100x=372
And, what is 372/100?
x=3.72 GB
So, assuming SSDs go by the same rules as HDDs (and I'm fairly sure they do, considering I got about 93% of the claimed capacity with my Intel SSD), you have a total of 3.72 GB of space on the smaller drive.
Using the same equation, that means your larger drive has 14.88 GB.
So, lets review the specs again.
Ubuntu takes up 5 GB of space. That means, split across 2 drives in a RAID 0 array, you have 2.5 GB taken up on each drive. This means that drive 1 has 1.22 GB left, and drive 2 has 12.38 GB left.
You have 1.22 GB of space left on drive 1-that means you can store a total of 2.44 GB of data before you have errors with the RAID controller not being able to split files and a put them in their proper place anymore.
You have 2 drives, which means you could do a RAID 1 array. RAID 1 is essentially keeping the drives totally backed up to each other. All changes on drive 1 happen to drive 2. It is essentially a continuous backup. But, keep in mind that now, there is no way you can fit regular Ubuntu on the first drive (sure, there are the Minimal CDs, but I haven't used one of those before, so I'm not sure how good they are).
Now, this may have been an extremely complicated and lengthy post, but here is the point: RAID is a way to make 2 or more drives act as one, but since you have different capacities on each one, you would have very little space. Also, there are 2 types of RAID controllers. Hardware (PCI cards) controllers are hassle free, usually. But, software controllers can be hard to configure and can be lost if you accidentally uninstall it or you do a clean install. Either way, they can get fairly pricey.
Basically, you would be much better off installing on your second drive, and using your first drive for backups of your Home directory. RAID has trouble working with different drive sizes to begin with, so I don't thing doing a RAID array on this would work out very well.
**TL;DR**-I don't think you can do what you want to do without running into some errors.
I hope this helps.

---

### Post by 2F4U on 2012-08-23
You can install with LVM. LVM is a logical volume manager, which allows you to view all physical volumes as one logical volume:

[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

