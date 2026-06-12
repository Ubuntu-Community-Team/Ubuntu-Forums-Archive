---
title: "HD Space management."
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by bhishan on 2009-10-28
Currently I am using Jaunty. I have a root "/" partition of 19 GB and swap "/swap" partition of 1 GB. I will be doing a clean install of Karmic as tomorrow (if it downloads fast enough, hope it will). I was planning to make three partitions "/", "/home" and "/swap", as a friend recommended. What are the benefits of doing this. I have allocated a total of 20 GB for Karmic, so can anyone recommend me the sizes that I should fix for these three partitions.

---

### Post by dabl on 2009-10-28
That's a good plan.  The benefits are:

swap -- you can suspend to disk, as long as the swap space is larger than the running system.

separate /home -- you can save your data there, and then if the OS gets totally borked up, you can reinstall the OS without disturbing your user data.

So, out of 20GB, if your computer's memory is 1GB, I would say make the swap space 1.3GB or something like that, so you can suspend to disk with no worries.

The root filesystem for the OS will need 6GB to be safe -- it starts out smaller than that, but grows with updates and new package installations.

So, 6 for the OS, 1.3 for swap, and the rest of it (~12.5GB) can be for your /home partition.  :)

---

### Post by bhishan on 2009-10-28
> **dabl said:**
> That's a good plan.  The benefits are:

swap -- you can suspend to disk, as long as the swap space is larger than the running system.

separate /home -- you can save your data there, and then if the OS gets totally borked up, you can reinstall the OS without disturbing your user data.

So, out of 20GB, if your computer's memory is 1GB, I would say make the swap space 1.3GB or something like that, so you can suspend to disk with no worries.

The root filesystem for the OS will need 6GB to be safe -- it starts out smaller than that, but grows with updates and new package installations.

So, 6 for the OS, 1.3 for swap, and the rest of it (~12.5GB) can be for your /home partition.  :)

Thanks a lot:)

---

