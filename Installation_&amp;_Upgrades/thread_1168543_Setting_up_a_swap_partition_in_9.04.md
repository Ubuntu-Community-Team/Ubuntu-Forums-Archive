---
title: "Setting up a swap partition in 9.04"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by Richardcavell on 2009-05-24
Noob alert; my apologies...

I've just set up Ubuntu 9.04 on a Macbook2,1, dual booting alongside OS X.

My internal hard disk has four partitions: The first is for EFI, the second contains OS X, the third is in ext3 format and contains Ubuntu, and the fourth is about 5 Gigabytes and is set up as a linux-swap partition.  I set it up using GParted but I don't remember ever telling Ubuntu to use it as swap.

How do I tell whether Ubuntu currently has a swap partition or file, and if so, where it is?  I want it to use the fourth partition as swap.  How do I do that?

By the way, Hibernate does not work at all, simply spitting out error messages and then halting the computer.  I suspect that this is related...

Richard

---

### Post by Moop on 2009-05-24
You can tell how much swap you have by running ```
cat /proc/meminfo
``` in a terminal and looking for the swaptotal value.

---

### Post by Richardcavell on 2009-05-24
I get:

SwapTotal:       5116676 kB

Which looks suspiciously like the size of the partition that I intended linux to use.  How can I confirm where it is located?  (Since the partition is not mounted in the usual way)?  I have never formatted this swap partition or done anything else to it.  Do I need to do that?  Is there a connection between this and my computer's inability to hibernate?

I have 1 Gig RAM, by the way.

Richard

---

### Post by Moop on 2009-05-24
You don't need to format a swap partition. You can install gparted (Partition Editor) and use that to see how your hdd partitions are setup. You will find it under System-Administration-Partition Editor after installation. 

There's probably a easier way of locating swap but I don't know what that would be.

---

### Post by drs305 on 2009-05-24
Another way to view your swap usage is with the command:
```
free -m
```
If it's all zeroes, your swap isn't recognized. If just the middle entry is 0, it means it's available but not being used.

The swap partition is normally designated in fstab. You can quickly check to see if it's listed there by running the following command:
```

grep "swap" /etc/fstab

```
If you don't get any lines returned, it's not listed in fstab but should be. 

If you don't have an entry, tell us the swap designation (sdXX, or better the UUID) and we can help you add the entry. You can get the UUID of the swap partition by running:
```

sudo blkid | grep "swap"

```

---

### Post by Richardcavell on 2009-05-24
Hi, 

This is what I get: 

> richard@richard-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           957        544        412          0         13        227
-/+ buffers/cache:        304        653
Swap:         4996          0       4996
richard@richard-laptop:~$ grep "swap" /etc/fstab
# swap was on /dev/sda4 during installation
UUID=316a7b38-2b96-4c68-8ac6-0ef2bb1a9487 none            swap    sw              0       0
richard@richard-laptop:~$ Seems like everything is in order then...?

Richard

---

### Post by drs305 on 2009-05-24
> **Richardcavell said:**
> Seems like everything is in order then...?


Yes, your swap should be working normally. Note: For future reference, if you ever need a 2-3 GBs of space, you can cut you swap partitiion's size down substantially.

Welcome to the ubuntu forums by the way.

---

### Post by kimharding on 2009-10-13
I have a swappartition of 2Gb but when I use
```
free -m 
```

I get:

kim@Ben-Macdui:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           986        840        146          0         47        388
-/+ buffers/cache:        404        581
Swap:            0          0          0
kim@Ben-Macdui:~$ grep "swap" /etc/fstab
UUID=17e9d245-a5bc-4ec8-9bbc-a5e000d5bb61 none swap sw 0 0
kim@Ben-Macdui:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           986        841        145          0         47        388
-/+ buffers/cache:        405        581
Swap:            0          0          0

The Swap Partition doesn't seem to be working. How do I correct this?

---

### Post by drs305 on 2009-10-13
> **kimharding said:**
> 

The Swap Partition doesn't seem to be working. How do I correct this?

You have it listed in fstab, but you also have to make sure the UUID is correct. If you moved or created a new swap partition, the UUID may not be correct.

Check the UUIDs on your system with the following command. The second one should just return 'swap' information if you want to filter the results:
```

sudo blkid
sudo blkid | grep 'swap'

```

Compare the results to what is posted in fstab. If they are not the same, change the fstab entry.

If you have to make a change, run these commands to 'refresh' swap:
```

sudo swapoff -a
sudo swapon -a

```

If they match, try running this command and see if the result also matches and if not post the result:
```

cat /etc/initramfs-tools/conf.d/resume

```

---

