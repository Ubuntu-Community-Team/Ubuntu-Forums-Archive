---
title: "Laptops and Partition Types"
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by DW5 on 2005-07-18
I'm pretty much a newbie to Linux.  I had a brief affair in the late 90s with Corel's version, but the apps just weren't quite up to my needs and I never could get Novel network drives configured.  I have had ubuntu installed for three weeks now (on a dual boot laptop) and haven't had to boot to windows yet.  I'm a convert (except for a known problem with a web database that only works with IE, but I'll deal with it).

I have a question that's more for curiosity but may help in the installation decisions that laptop users face.  

I installed ubuntu using ext3 partitions--I liked the idea of journaling. However, now after three weeks, I am wondering how much more my disk drive is running under ext3 than it would be under ext2.  

I don't run for very long under battery power -- 1.5- 2 hours at most, but it would create an issue for laptop users who really need to eke the most out of their batteries.

Thought I would see what those who know better had to say--is there a better partition type to use when installing linux to laptop?

---

### Post by luca_linux on 2005-07-18
Adding the "noatime" option can help to reduce hd access and so to speed up the performance and to reduce battery consumption.
Just mount your root (and eventually any other partition for data if you have one) with this option.
Your /etc/fstab should look like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,**noatime**,errors=remount-ro 0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

```

---

### Post by DW5 on 2005-07-19
Does adding the noatime flag, which as I understand if from the man page, stops logging accesses to that file system, essentially disable the ext3 partition type features and make it act like an ext2, or are those ext3 journals something different?

---

### Post by luca_linux on 2005-07-19
No, there are other things too.

---

### Post by DW5 on 2005-07-26
I've been out of town, but am checking in.  

I guess the question is:  If you run a ext3 filejsystem with noatime set, should you really just be running an ext2 filesystem, or is there a good reason to run ext3 on a laptop with noatime set? (again, this is to provide for getting the most efficiency from the machine to preserve battery).

---

### Post by somez on 2005-07-26
[QUOTE=DW5]I'm pretty much a newbie to Linux.  I had a brief affair in the late 90s with Corel's version, but the apps just weren't quite up to my needs and I never could get Novel network drives configured.  I have had ubuntu installed for three weeks now (on a dual boot laptop) and haven't had to boot to windows yet.  I'm a convert (except for a known problem with a web database that only works with IE, but I'll deal with it).

I have a question that's more for curiosity but may help in the installation decisions that laptop users face.  

I installed ubuntu using ext3 partitions--I liked the idea of journaling. However, now after three weeks, I am wondering how much more my disk drive is running under ext3 than it would be under ext2.  

I don't run for very long under battery power -- 1.5- 2 hours at most, but it would create an issue for laptop users who really need to eke the most out of their batteries.

Thought I would see what those who know better had to say--is there a better partition type to use when installing linux to laptop?[/QUOTE]

For the IE under Linux problem try Crossover Office, wich you can buy from [www.codeweavers.com](www.codeweavers.com).

---

### Post by luca_linux on 2005-07-26
[QUOTE=DW5]I've been out of town, but am checking in.  

I guess the question is:  If you run a ext3 filejsystem with noatime set, should you really just be running an ext2 filesystem, or is there a good reason to run ext3 on a laptop with noatime set? (again, this is to provide for getting the most efficiency from the machine to preserve battery).[/QUOTE]
 No, ext3 with noatime option is not an ext2, because the journaling system is not disabled by noatime.

---

### Post by DW5 on 2005-07-30
Thanks for the info.

DW

---

