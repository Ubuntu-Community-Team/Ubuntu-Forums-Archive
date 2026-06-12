---
title: "Old Hard Drive and Swap"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by PipM on 2008-12-09
I'm planning to buy a new desktop PC this month (probably with Vista *sigh*) but I want to hook up the hard drive from my old computer - a magnificent 8 Gb - to install Ubuntu and have a muck around on there.

Do you think this would be possible and, furthermore, could the Ubuntu OS drive and the swap partition actually be on physically different disks. (e.g. if my RAM is 4Gb, should I create a swap partition of about 8Gb on the disk that comes with the machine?)

I'm sorry if I sound a bit n00bish, but I literally haven't done anything like this before.

---

### Post by jenkinbr on 2008-12-09
That would work just fine.

You will have to use manual partitioning to put swap on a seperate disk, but other than that, what you are asking is not only possible, but a good idea.

Regarding swap size, do you know what architecture your new computer will be running?  If it is 64 Bit, then you will be fine with 8GB of swap (a bit excessive, if you ask me, I would probably go for 5 or 6 GB given the amount of ram you have.  However, if you are getting only a 32 bit computer, adding swap won't help any unless you plan on hibernating, as the maximum ram supported is 3.5GB for 32-bit. (Somebody PLEASE correct me if I am wrong here...)

If you have less than 4GB of ram, I would create the swap so that it has 2x your installed RAM...

---

### Post by cdtech on 2008-12-09
> **PipM said:**
> Do you think this would be possible and, furthermore, could the Ubuntu OS drive and the swap partition actually be on physically different disks. (e.g. if my RAM is 4Gb, should I create a swap partition of about 8Gb on the disk that comes with the machine?)

Sure you could use different disk for your "swap". You wouldn't need that much "swap" the thing to keep in mind is the amount of memory you acually need for all the programs you run at once to be placed on your "swap" partition during hibernate.

Using swap is the way the Linux kernel handles the virtual memory subsystem thats incorporated into the code.

The only reason there is virtual memory in the first place is that you may not have enough RAM for all the programs running at once, and disk space was cheap. Swap is still tightly integrated into the kernel code and there should be some swap space used for this purpose. The kernel code runs smoother with some swap space. You'll also need swap if you plan to Hibernate to disk, so think about how much space you'll need to store your running programs to disk.

Hope this helps ya.......

---

### Post by jenkinbr on 2008-12-09
> **cdtech said:**
> Sure you could use different disk for your "swap" but it would have to be an "ext2/3" filesystem......

Isn't the swap patition supposed to be formatted as SWAP, not ext2/3?

---

### Post by taurus on 2008-12-09
> **cdtech said:**
> Sure you could use different disk for your "swap" but it would have to be an "ext2/3" filesystem. 

Swap uses ext2/3 filesystem!  :confused:

---

### Post by logos34 on 2008-12-09
> **jenkinbr said:**
>  I would probably go for 5 or 6 GB given the amount of ram you have.  However, if you are getting only a 32 bit computer, adding swap won't help any unless you plan on hibernating, as the maximum ram supported is 3.5GB for 32-bit. (Somebody PLEASE correct me if I am wrong here...)

+1

yeah, i believe 32 bit can handle just under 4 gb ram (even less in windows).

If you're getting a new machine with dualcore cpu, then it will be x64 capable, so you're covered--get the amd64 ubuntu install iso

like jenkinbr says, ~5 gb swap should work if you also want to hibernate.  If not you can reduce that dramatically (most of the time you will probably never use swap, or if you do it will never exceed ~1.5 gb)

---

### Post by PipM on 2008-12-09
Ah, that's awesome help - glad I joined this now!

Also, I haven't actually decided on a PC yet so I don't know what architecture it will be but thanks for covering all bases. I should use FAT32 for partitioning a disk for sharing files between both OS's right?

---

### Post by logos34 on 2008-12-09
> **PipM said:**
> I should use FAT32 for partitioning a disk for sharing files between both OS's right?

no need to anymore--ubuntu natively supports read and write to NTFS.  (ntfs-3g driver).  And there's fs-driver for windows (read+write ext2/3).  So I'd just leave it.

---

### Post by cdtech on 2008-12-09
sorry, my bad

---

### Post by cdtech on 2008-12-09
> **jenkinbr said:**
> Isn't the swap patition supposed to be formatted as SWAP, not ext2/3?

I do stand corrected. Didn't mean to put that in there. You can also use NTFS and mount the Window's pagefile.sys as your swap......sorry

---

### Post by linux_tech on 2008-12-09
If you have low memory, then you should set up a swap file. I like to use 2 x the memory in this case . So if you have 256 mb RAM, then you should have a swap file of 512MB. If you have more memory, then swap becomes less
of an issue.
 more on swap files here-
[http://manpages.ubuntu.com/manpages/intrepid/man8/mkswap.html](http://manpages.ubuntu.com/manpages/intrepid/man8/mkswap.html)
[http://manpages.ubuntu.com/manpages/hardy/man8/swapon.html](http://manpages.ubuntu.com/manpages/hardy/man8/swapon.html)

---

### Post by jenkinbr on 2008-12-09
He was talking 4GB, so this shouldn't be a problem...

---

### Post by PipM on 2008-12-21
> **jenkinbr said:**
> Isn't the swap patition supposed to be formatted as SWAP, not ext2/3?

How do I format a partition on my original disc as SWAP? Can I do this from Windows on the same disc or will I have to do it when I have installed Linux on my other hard disc?

---

