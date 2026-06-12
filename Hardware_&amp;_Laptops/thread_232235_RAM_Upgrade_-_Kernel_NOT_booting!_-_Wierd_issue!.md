---
title: "RAM Upgrade - Kernel NOT booting! - Wierd issue!"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by daller on 2006-08-08
Hi There,

Just upgraded my RAM on my laptop

Had: 256MB

Has: 1024MB (2x512MB)

Somehow, it doesn't seem like a hardware-issue!

With 256MB everything works great!

With 512MB the kernel is not loading! (But I can see that the BIOS has recognized the RAM!)

Now the weird part comes:
- If I try to run of a Live CD, it works great! (Running with 512MB)

Can somebody point me in the right direction?

I know that a clean-install would probably work (since the Live CD works) - But I would prefer an easier way!

Please help!

---

### Post by x64Jimbo on 2006-08-08
Would booting the rescue mode (from GRUB) make any difference?

---

### Post by daller on 2006-08-08
> **x64Jimbo said:**
> Would booting the rescue mode (from GRUB) make any difference?

Well, it boots the kernel, but reports that "/dev/null" among other gives "Segmentation Fault"

---

### Post by daller on 2006-08-08
Well, my girlfriend got home, and I testet the "defective" RAM in her laptop...

...And that worked!

Now I'm even more confused!

I've tested the 2 sticks I recieved in the same slot in MY laptop! - 1 working, and 1 NOT working.

Weeee! - Now I have 512MB of RAM in my laptop! - It's a double :)

But I don't understand why the stick that didn't work in my laptop, work in hers!

---

### Post by x64Jimbo on 2006-08-08
Where did you order your memory from? Is it possible that the timing is wrong for your motherboard?

---

### Post by daller on 2006-08-09
> **x64Jimbo said:**
> Where did you order your memory from? Is it possible that the timing is wrong for your motherboard?

It's out of the question...

The 2 blocks are identical!

- one works, another doesn't! (on my laptop!)

The one that doesn't work on my laptop, works on my girlfriends laptop.

Anyway, don't waste time on this issue! - I've installed the block in her laptop permanently, and that seems to work!

---

