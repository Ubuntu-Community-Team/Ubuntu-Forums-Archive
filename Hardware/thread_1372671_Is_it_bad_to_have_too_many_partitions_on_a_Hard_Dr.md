---
title: "Is it bad to have too many partitions on a Hard Drive?"
date: 2010-01-04
forum: Hardware
---

### Post by Vignesh S on 2010-01-04
The question says it all, will having too many partitions on my hard drive wreck it faster than if it only had say, 2-3?

---

### Post by gabo.cr on 2010-01-04
How many is too many?
Why do you need so many?

---

### Post by llama320 on 2010-01-04
I don't see any reason that more partitions would slow down your machine -- note that if you want more than 4 you'll have to make one of them extended (rather than primary)

---

### Post by Joe Ker1086 on 2010-01-04
There is no problem with havin a lot of partitions. It is just sectioning off the drive but not causing any hardware changes so it will not fail faster. I user 4 partitions  ( /boot / swap and /home) with no performance problems. You also give yourself a lot of flexibility with multiple partitions.

---

### Post by sisco311 on 2010-01-04
> **gabo.cr said:**
> How many is too many?
Why do you need so many?

+1

of course **too many** is bad, too many of anything is bad, that's what too many means... to many is precisely that quantity which is excessive.

:)

---

### Post by Vignesh S on 2010-01-04
> **gabo.cr said:**
> How many is too many?
Why do you need so many?

How does 7 sound? (2 are unintended when I tried to install moblin, but it went wrong and I'm in a bit of strife in terms of getting rid of them)

Toshiba and Win 7 don't help. 2 are for win 7, 1 for recovery, 1 Ubuntu ext4, 1 swap, 2 random partitions no more than 2MB each.

I am just a little on edge about the random partitions, thats all.

---

### Post by sisco311 on 2010-01-04
> **Vignesh S said:**
> How does 7 sound? (2 are unintended when I tried to install moblin, but it went wrong and I'm in a bit of strife in terms of getting rid of them)

Toshiba and Win 7 don't help. 2 are for win 7, 1 for recovery, 1 Ubuntu ext4, 1 swap, 2 random partitions no more than 2MB each.

I am just a little on edge about the random partitions, thats all.

Open a terminal (Applications -> Accessories -> Terminal)

and please post the output of the following command:
```
sudo fdisk -l
```

---

### Post by Vignesh S on 2010-01-04
```
vignesh@vignesh-laptop:~$ sudo fdisk -l
[sudo] password for vignesh: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaba581d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       16480   130832336    7  HPFS/NTFS
/dev/sda3           29170       30402     9896960   17  Hidden HPFS/NTFS
/dev/sda4           16481       29169   101924392+   5  Extended
/dev/sda5           28649       29169     4184901   82  Linux swap / Solaris
/dev/sda6           16481       28648    97739397   83  Linux

Partition table entries are not in disk order
vignesh@vignesh-laptop:~$ 


```

Hope that helps

---

### Post by gabo.cr on 2010-01-04
That's about right.
That's a basic partitioning for both systems.

---

### Post by Vignesh S on 2010-01-04
What about /dev/sda1? That message below it doesn't look too good :-S

---

### Post by gabo.cr on 2010-01-04
I would not worry so much about that.
The only way (I think) to fix this, is by installing everything again.
But you should not have any problems because of that.
Many years ago that was considered a problem due to possible data loss.
But Ubuntu is "smart" enough now.

---

### Post by Vignesh S on 2010-01-04
Data loss isn't a problem for me (I'm not putting anything important on the laptop, so its alright). I'm more worried about the fact that the HDD could crash, and that a very important tool for me would be unusable while I was getting replaced. 

Good to hear that Ubuntu won't cause me any heart ache in terms of that though. I'll post up what gparted has to say sometime soon

---

