---
title: "swap? no swap"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by homeslice on 2006-06-28
I've encountered a weird issue with my swap partition. I installed Dapper a few weeks ago on my Dell e1505/6400 and (after one crash during the install) everything appeared to go fine. I left space for the swap partition as well as a Windows partition, which I later installed without any apparent issues. 
 However, despite the fact that the 1024MB of swap space remains allocated and detectable by fdisk, it's not being used. Here's the relevent line of fdisk output:
 
[FONT="Lucida Console"]/dev/sda2            3407        3534     1028160   82  Linux swap / Solaris[/FONT]

but /proc/meminfo contains:
[FONT="Lucida Console"]SwapTotal:           0 kB
SwapFree:            0 kB[/FONT]

dmesg | grep swap also lists:
[FONT="Lucida Console"]
Jun 28 10:37:21 localhost kernel: [17179593.612000] Unable to find swap-space signature[/FONT]

I've tried [FONT="Lucida Console"]$sudo swapon -a[/FONT]
 but this yields
[FONT="Lucida Console"]swapon: /dev/sda2: Invalid argument[/FONT]

Finally, /etc/fstab contains
[FONT="System"]/dev/sda2       swap            swap    sw              0       0[/FONT]


 Worst of all, if I exceed the 512MB of native memory on my machine by having more than a few apps open at one time, the entire systems hangs (or at least becomes extremely slow and, eventually, completely unresponsive).
 I'm pretty noob. Any ideas? Thanks!

---

### Post by PvSinNL on 2006-06-29
I'm not sure whether this is the cause of the problem you describe, but on my system /etc/fstab reads:
```
/dev/hda6    **none**     swap    sw   0    0

```
In other words, the mount point is specified as "none".
And man fstab yields:
> The second field, (fs_file), describes the mount point for the filesystem.  For swap partitions, this field should be specified as &#8216;none&#8217;.

You might also try to add a swap file on one of your partitions as a (temporary) fix. See [https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq") for more information.

---

### Post by homeslice on 2006-06-29
thanks - I tried it, but the behavior appears to remain unchanged. Any other thoughts?

---

### Post by kEpEx on 2007-02-14
> **homeslice said:**
> I've encountered a weird issue with my swap partition. I installed Dapper a few weeks ago on my Dell e1505/6400 and (after one crash during the install) everything appeared to go fine. I left space for the swap partition as well as a Windows partition, which I later installed without any apparent issues. 
 However, despite the fact that the 1024MB of swap space remains allocated and detectable by fdisk, it's not being used. Here's the relevent line of fdisk output:
 
[FONT="Lucida Console"]/dev/sda2            3407        3534     1028160   82  Linux swap / Solaris[/FONT]

but /proc/meminfo contains:
[FONT="Lucida Console"]SwapTotal:           0 kB
SwapFree:            0 kB[/FONT]

dmesg | grep swap also lists:
[FONT="Lucida Console"]
Jun 28 10:37:21 localhost kernel: [17179593.612000] Unable to find swap-space signature[/FONT]

I've tried [FONT="Lucida Console"]$sudo swapon -a[/FONT]
 but this yields
[FONT="Lucida Console"]swapon: /dev/sda2: Invalid argument[/FONT]

Finally, /etc/fstab contains
[FONT="System"]/dev/sda2       swap            swap    sw              0       0[/FONT]


 Worst of all, if I exceed the 512MB of native memory on my machine by having more than a few apps open at one time, the entire systems hangs (or at least becomes extremely slow and, eventually, completely unresponsive).
 I'm pretty noob. Any ideas? Thanks!


I haved the same problem than you... and i follow the tutorial that tells last guy... and i made a swap file and Works!!, all fine, but i have a partition that supose to do the work of swap... then.. i apply the same command to that partition than used to make swapable the file...


and!!! works!!!

now i left use the swap file, and i recover to use my swap partition :D:D

how i do??

my partition is "/dev/hda2"

then i exec: 

```
mkswap /dev/hda2
swapon /dev/hda2
```

and that's all!!

test it.. and tell us!

....... sorry by my english :)

---

### Post by pinkunicorn on 2007-02-14
mkswap and swapon solved my problems. I had only tried swapon before, but that wasn't enough by itself.

---

### Post by cari on 2007-12-27
Thanks kEpEx , I also tried mkswap only. after executing swapon everything works:popcorn:

---

