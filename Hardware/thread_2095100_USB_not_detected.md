---
title: "USB not detected"
date: 2012-12-15
forum: Hardware
---

### Post by SumitM on 2012-12-15
I'm running Linux Mint Live disk with persistence. I installed NTFS configuration tool to understand why my USB enclosed HDD get corrupted every time I unmount it. Almost all Linux flavors detect my USB enclosed HDD (This HDD is a laptop internal HDD with SATA port) as internal HDD. Is there any solution to force linux to detect this USB enclosed HDD as External/portable HDD? I tried Ubuntu 12.04, Ubuntu 12.10 and Linux Mint 14 and they all corrupt my HDD after unmount operation. I even try to restart linux while HDD is still mounted....STILL CORRUPTED. It's working fine with windows xp, 7 and windows 8. Please help me.... it's HITACHI 250GB laptop internal (3.5") HDD.

---

### Post by DuckHook on 2012-12-15
> **SumitM said:**
> I'm running Linux Mint Live disk with persistence. I installed NTFS configuration tool to understand why my USB enclosed HDD get corrupted every time I unmount it.

If running your OS from a USB stick/HDD, you cannot just unmount. Since your OS is running from the device, it continues to hold open files (or file headers) to the device. You must shutdown properly and completely (to power-down or at least halt state) before removing USB stick/HDD. Or do I misunderstand? Are you running the OS from one USB stick and mounting the HDD drive from another separately? If so, please provide full description of your HW setup.

Also, what do you mean by "corrupted". Please give detailed description of problem. Is it that you simply can't read the disk? Partition table missing?

---

### Post by Bucky Ball on 2012-12-15
[I]Posts moved to own thread in [B]Hardware

[/B][/I]@ SumitM: Welcome to the forums. Please do not post issues on an existing thread. This is known as 'hijacking' and not encouraged. It confuses the original issue and is not fair to original poster or helpers. ;)

Your post was also 30 posts deep. Moving it to a new thread will improve your chances of getting help. 

Good luck with it ...

---

