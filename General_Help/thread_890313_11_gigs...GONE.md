---
title: "11 gigs...GONE?"
date: 2008-08-14
forum: General Help
---

### Post by VivaLaEva on 2008-08-14
Alright, so I made a thread awhile ago about royally boning my OS, again, by way of partitions.

After decided there was no fix, I accepted the fact that I'd have to do yet another clean install [but hey, I'm learning!].

Here's the problem:

My laptop's internal hard drive is 160 gigs.  It's nice for a 14-month-old laptop, let me tell you.  Anyway, 160 total gigs.  What happened was I managed to erase and un-allocate my partitions while trying to write a new flag to what was to be the secondary, Vista partition.

What I didn't realize was that this space was only 149 gigs.
I rebooted with the gParted LiveCD, and tried to completely delete the partition, yadda yadda yadda...but I'm stuck at 149 gigs.  The other 11 went...where now?

Is there any way for me to find those? 'Cause I realize that, yeah, 11 gigs isn't a lot, but it bothers me that it's lurking about somewhere around...

To make things worse, when I try booting without a CD at all, GRUB is still hangin' out.  But it goes directly to an Error 22.

So does anybody know how I can find and free up that space? GParted doesn't see it :(

Thanks!!

---

### Post by yabbadabbadont on 2008-08-14
It didn't go anywhere... you have not considered that one gigabyte for a drive manufacturer is 1,000,000,000 bytes.  Linux tools use a power of 2 based gigabyte.  (1024*1024*1024 = 1073741824)

If you divide 160,000,000,000 by 1073741824, you will get 149.  ;)

---

### Post by jerome1232 on 2008-08-14
Just to throw in this isn't a Linux specific thing, you will find the same under Windows NT, BSD, Mac, etc...

---

### Post by VivaLaEva on 2008-08-14
> **yabbadabbadont said:**
> It didn't go anywhere... you have not considered that one gigabyte for a drive manufacturer is 1,000,000,000 bytes.  Linux tools use a power of 2 based gigabyte.  (1024*1024*1024 = 1073741824)

If you divide 160,000,000,000 by 1073741824, you will get 149.  ;)

The problem with this is, when I last screwed up my partitions and deleted everything, gParted showed the total unallocated, unformatted space as 160 gigs.

And now it's only showing as 149.
So.

---

### Post by rob1101 on 2008-08-20
are you sure you not mixing up **GB** and **GiB** yabbadabbadont gives the math to expain the differance 160 GB = 149 GiB. Where does it read 149 GB exactly? The GiB measurement kind of threw me at frist too :)

---

### Post by VivaLaEva on 2008-08-20
Gah, I'd take a screenshot but I went and re-partitioned my harddrive anyway [Ubuntu, XP or TinyVista or whatever I can cram on there, potential 2nd linux-based OS, and swap-space]...but I just checked again, and it does read GiB!

Which is odd, 'cause like I said -- last time I went and boned my partitions, it told me the one single chunk of unallocated space was 160 GB..and I guess now it's 149 GiB.  Which, I guess, is the same [thanks yabbadabbadont]...weird O.o

And weirder, last time I boned my partitions and had to erase everything [buggy version of TinyXP, ick], when I tried booting, it just said No Operating System found.  After this weird [potential] dissapearance, the Grub was still hanging out in there somewhere, at least enough for an Error 22, which further led me to believe I was missing a chunk.

Odd stuff.

Thanks to the three of you, though ^-^

---

### Post by rob1101 on 2008-08-20
that was probably due to invalid grub entries. You can look at the ones you have now and add new ones in the grub menu.lst. it is located here

```
/boot/grub/menu.lst
```

just look for the part that looks like this.

**Note: making changes to this file can give you a system that does not boot.** Hence your no OS found error

```
title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=95e2e96b-08b3-4f45-9aea-2cab2d584bdd ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=95e2e96b-08b3-4f45-9aea-2cab2d584bdd ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

```

---

