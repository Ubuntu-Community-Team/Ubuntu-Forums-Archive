---
title: "Reinstalling 8.10"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by jstrowe on 2009-05-28
My daughter's dual boot system (Vista and Ubuntu 8.10) stopped working with only distorted graphics on the screen after booting and no response from the mouse or keyboard. I don't know what, if anything, she may have done to damage the system.

I tried to re-install from the CD-ROM, but when it gets to the partitioner, it wants to create a new partition for it. I thought that "manual" would allow me to re-install to the same partition. However, when I select manual, the display of what the disk will partitioned as shows it using the whole disk. I have not gone past that point since I do not want to disturb the existing partitions.

How do I re-install to the same partition?

Thanks,
John

---

### Post by albinootje on 2009-05-28
> **jstrowe said:**
> However, when I select manual, the display of what the disk will partitioned as shows it using the whole disk. 

Strange :(

Is MS-Vista not giving a distorted screen ?
Can you boot successfully from the "recovery mode" in Ubuntu ?

---

### Post by merlinus on 2009-05-28
It may be that vista is hosed.  You might use gparted live cd to look at what partitions it finds.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by jstrowe on 2009-05-28
Vista runs correctly. Of course, that means painfully slow which is why I installed Ubuntu.

I can boot in recovery mode. However, I tried all the selections that looked like they might fix something, anything, to no avail. I can run from the CD, however, it uses the display at a much lower resolution than the installed version was using.

The partitioner correctly identifies the existing partitions on the disk. It wants to create a new partition for Ubuntu, which I don't want to do. I suspect that manual might let me use the existing partitions. However, I don't want to risk destroying data on someone else's machine.

Thanks,
John

---

### Post by merlinus on 2009-05-28
Forgive my confusion, but it seems that using manual partitioning will allow you to reinstall into the existing ubuntu partition.  Is that not what you are wanting?  Is there not a choice as to which partition into which to install?

If there is no separate /home partition, then indeed all data that is currently there will be lost, unless of course you back it up.

---

### Post by albinootje on 2009-05-28
> **jstrowe said:**
>  The partitioner correctly identifies the existing partitions on the disk.


Can you post the output of the following :
```

sudo fdisk -l

```
Or.. better a screenshot, after running :
```

sudo gparted

```
In the latter we can easily see how much space is used on the partitions.

---

### Post by jstrowe on 2009-05-28
> **merlinus said:**
> Forgive my confusion, but it seems that using manual partitioning will allow you to reinstall into the existing ubuntu partition.  Is that not what you are wanting?  Is there not a choice as to which partition into which to install?

If there is no separate /home partition, then indeed all data that is currently there will be lost, unless of course you back it up.
I guess that's largely my question. When I clicked on manual, the display of the new disk partitioning showed the entire disk being used for Ubuntu. That's not what I wanted to do. I did not want to move forward at that point since it is not my machine. If I delete my own data, I just feel stupid. Besides, I've got everything important backed up. However, if I delete someone else's data I really feel bad.

If you can tell me that it really works that way, I will try it. I just want to be careful.

Thanks,
John

---

### Post by jstrowe on 2009-05-28
> **albinootje said:**
> Can you post the output of the following :
```

sudo fdisk -l

```
Or.. better a screenshot, after running :
```

sudo gparted

```
In the latter we can easily see how much space is used on the partitions.
I can try this, but my daughter's asleep now so I probably won't have a chance to get back to it until the weekend.

Thanks,
John

---

### Post by merlinus on 2009-05-28
IIRC, selecting manual partitioning offers more options than using the entire disk.  You may wish to have another look, because one should be to use the partition where ubuntu is currently installed.

---

