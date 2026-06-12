---
title: "Swap needed with large amount of RAM"
date: 2008-06-01
forum: Hardware
---

### Post by Seventh Reign on 2008-06-01
I understand that typically the Swap partition is supposed to be double your amount of RAM.  I have 8gig of RAM .. do I really need a 16gig Swap .. or any Swap at all?

---

### Post by TroyDowling on 2008-06-01
Good grief... Slap Ubuntu on a ramdisk and see it whirl. =] Personally I would be inclined to say no, but it may be required to hibernate/suspend or something like that. I doubt you really need to double it in this case though. On my first few installs ever I didn't use any swap and that was only with a gig of RAM on my old computers. Now, however, I follow the double-the-RAM swap size. You'll have to up some other stats of that machine. I take it it's a server of some sort?

---

### Post by nick_h on 2008-06-01
> but it may be required to hibernate
Yes, during hibernate the memory is stored in the swap partition.

---

### Post by Seventh Reign on 2008-06-01
Nah not a server .. just a Gaming Desktop.

3.0ghz Pentium Dual Core 
8,192MB DDR2 RAM (4-2GB Chips)
320GB SATA-300 HDD (Ubuntu 8.04 x64 and Sabayon 3.4f)
250GB SATA-300 HDD (Windows)


Suspend and Hibernate arent really an issue for me.

---

### Post by Seventh Reign on 2008-06-03
I read this on the Mint Forums.

*[SIZE="2"]"Swap partitions don't need to be any larger than 2X your system ram. And, the sum of system ram and swap shouldn't exceed 4 Gig. If it does, reduce the swap partition size to get back to 4 Gig. or less. If you have 4 Gig. of ram on a 32 bit system like Mint, make a very small swap partition anyway, as the kernel expects to have a swap partition available. Not having a swap partition slows the kernel down in certain situations. For this purpose, there is no need for the swap partition to be over 256 KB at most."[/SIZE]*

Says to make a small swap for a 32 bit system, but I'm running   x64.

---

### Post by jespdj on 2008-06-03
A 32-bit system can't address more than 4 GB RAM (at least, not without special tricks such as [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension")) - that's why that message from the Mint forums says that the sum of physical and swap shouldn't exceed 4 GB. It does not apply to 64-bit systems.

---

