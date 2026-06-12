---
title: "How to partition with gparted"
date: 2010-06-16
forum: Hardware
---

### Post by SirKablaam on 2010-06-16
I've recently wanted to partition my /dev/sda1 partition so i can be able to dual boot vista with ubuntu (i miss my games too much :P). The problem is, I run gparted (boot) from the live cd that i created earlier. when i try to boot it, i get a whole list of options and every one i try, my screen goes completely black and unusable, requiring me to restart my computer. can anyone help me out here?

---

### Post by wojox on 2010-06-16
When you get to your list of options, try pressing F6 and selecting (spacebar) nomodeset and then Try Ubuntu without...

---

### Post by Mark Phelps on 2010-06-17
> **SirKablaam said:**
> I've recently wanted to partition my /dev/sda1 partition so i can be able to dual boot vista with ubuntu ... 

Not a good idea to do with with GParted as you run the risk of corrupting the Vista OS partition and rendering it unbootable.

Better approach is to go into the Vista Disk Management utility and use it to shrink the Vista partition to make room for Ubuntu.

Then when you reboot using the Ubuntu CD, selected the "user largest free space" option to install to the unallocated space.

---

