---
title: "effecient dual boot partiction set"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by borisattva on 2006-01-26
i have 2 hard drives

1 80gb
2 250gb

as much as i tried to avoid it i will need to bring back windows in a dual boot. so i plan to do this

80gb
 1 80bg partition
 - winxppro OS files

250
 1 150gb partition
 - use auto allocate free space for ubuntu
 2 100gb partition
 - winxp - Dox & Sets folder


my logic behind this is that if the OS and the user data are on separate drives it would free up the drive access load and make things run a little faster - does this make sense to anyone?

but then i wonder if using another harddrive for the /home on linux would yield the same benefit. would it?

---

### Post by amohanty on 2006-01-27
> 80gb
1 80bg partition
- winxppro OS files
You could probably get by with just 10 G.
I only have 2 80Gs which I partition this way
HDD1: XP 30G (for gaming only)
         Ubuntu /boot 500M (is overkill but thats ok)
         Ubuntu / rest
HDD2: Ubuntu swap 4G
         Ubuntu /home 55G
         Fat32 rest mounted to Ubuntu /home common for game state files.

quite frankly. with todays hw I dont think you will see much of a performance difference.

Just my <insert currency here>.02

AM

---

