---
title: "Installed in wrong partition!"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by optikal1 on 2009-07-09
Hello!

I am new to ubuntu. Finally decided to give it a go, after hearing heaps of praise. But looks like I screwed up in the installation itself. Here is what happened.

I have a windows machine (desktop) where I have 3 partitions, C:, D: (where I have all my data) and E: (9 GB), which was empty space and I made it into partition to install ubuntu. During the install phase, when prompted to repartition, I chose the default setting. The installation was fine and ubuntu started without the disk on reboot. However, when I clicked to install the updates, it said, not enough space. I realized that it has borrowed some space from D: (about 3GB) rather than installing on E:. So there is not enough space in its root directory.

So what do I do now? Do I have to uninstall ubuntu (I actually don't know how) and reinstall using some other settings? Why did it not pick E: which was completely empty? Is there some easier way to fix this mess?

Thanks for the inputs!

---

### Post by tommcd on 2009-07-10
Open a terminal (applications > accessories > terminal) and run:
```

df -h

```
and:
```
sudo fdisk -l
```
Post the output of both of those commands here.
Assuming that you are right, that Ubuntu installed on a 3GB partition and you are out of space, here is what I would do:
 Reinstall Ubuntu. Choose manual partitioning. Delete the 3GB partition Ubuntu is installed on and delete the partition that you identified as the 9GB "E drive" in Windows. This should then leave 3 + 9 = 12GB free space.
Then create a 1GB swap partition. Then use the remaining space on the drive for the Ubuntu root partition. Then proceed with the installation as you did before.
Since you just installed Ubuntu, it won't cost you much time or effort to reinstall Ubuntu as I described. 

Later, when you (hopefully) decide to switch to Ubuntu from Windows, you can backup the data on the D drive, then delete that, then use that space to create a separate home partition for Ubuntu. Right now, with only 12GB allocated for Ubuntu, I would just create a root and swap partition for simplicity, and to optimally use the limited space.

---

