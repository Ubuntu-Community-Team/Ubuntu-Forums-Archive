---
title: "Linux Swap"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by shanghaipi on 2005-06-22
So, a couple of months ago I installed kubuntu64 and reinstalled windows xp because of the many bugs in the amd 64 edition.  

Anyhoo, I installed the 32 bit version of Kubuntu yesterday and, after reading and downloading many gtk apps which I liked, just installed Ubuntu off of the cd over Kubuntu.  

Now, initially, when checking my system states, I noticed 1.5 gigs missing from my hard drive.  I thought it was the remainder of my Kubuntu system chilling on my drive.  So I downloaded GParted and checked it out.  

So my question is, what actually is this Linux-Swap that takes up 1.5 gigs of HD space?

---

### Post by hw-tph on 2005-06-22
The swap partition or swap file if you prefer to use that is a means for the kernel to move data from RAM to disk when your RAM is being filled up. Memory pages that have not been used recently get moved to disk to make room for new memory pages. If the swapped out (on-disk, in the swap partition or swap file) pages are needed they are moved into RAM again by the kernel.

With Windows you have a swap file instead of a swap partition but the most common way of doing it in Linux is having a swap partition. In short, it sort of increases your available memory.


Håkan

---

### Post by shanghaipi on 2005-06-22
I see.  So would the swap partition would take care of internet caches and all available temporary memory as well?  Because 1.5 gigs of backup memory is a lot.

---

### Post by mrcbrown on 2005-06-22
[QUOTE=shanghaipi]I see.  So would the swap partition would take care of internet caches and all available temporary memory as well?  Because 1.5 gigs of backup memory is a lot.[/QUOTE]
 Internet cache is browser specific - swap deals mainly with system memory swap. If you want smaller don't have Ubuntu auto-parition your drive. I have a 200GB drive, I just let ubunutu have it's way with it :)

---

### Post by shanghaipi on 2005-06-22
Well, I have a 60 gig hard drive, I don't think 1.5 gigs should be a problem.  Unless I don't need all that memory swapping.  But seriously 1.5 gigs?  Ubuntu better be working a 40 hour a week job on that sucker and deposit that smack in my bank account.

---

