---
title: "Questions about Swap"
date: 2008-08-21
forum: General Help
---

### Post by Jackelope on 2008-08-21
I had an installation of Linux Mint on a 16 GB partition. I had 700mb Swap and 512mb ram. The operating system didn't use swap. Ever. I thought this was normal because I never exceeded my 512mb ram. However, I recently reinstalled Mint. This time I installed it with 500mb swap. It runs a lot faster now, and 30-100mb of swap are used on average along with 200-300mb of ram (running firefox, skype, etc.) So I have 2 questions...

1. Does the size of my swap partition have anything to do with how much of it is used? Would having the larger swap of 700mbs cause my swappiness to decrease? 

2. Would increasing my swap partition increase performance? I've read that 2x the amount of ram you have works best, but since its working so well now I'm not sure I want to play with it too much :)

Thanks for any explanations/advice.

---

### Post by WRDN on 2008-08-21
> **Jackelope said:**
> I had an installation of Linux Mint on a 16 GB partition. I had 700mb Swap and 512mb ram. The operating system didn't use swap. Ever. I thought this was normal because I never exceeded my 512mb ram. However, I recently reinstalled Mint. This time I installed it with 500mb swap. It runs a lot faster now, and 30-100mb of swap are used on average along with 200-300mb of ram (running firefox, skype, etc.) So I have 2 questions...

1. Does the size of my swap partition have anything to do with how much of it is used? Would having the larger swap of 700mbs cause my swappiness to decrease? 

2. Would increasing my swap partition increase performance? I've read that 2x the amount of ram you have works best, but since its working so well now I'm not sure I want mt play with it too much :)

Thanks for any explanations/advice.

Regarding the first question, the size of the swap partition can affect the usage. For example, if you have 512Mb RAM, and are using 100% of it, and have a 550Mb swap partition, when you enter hibernation, you are left with 38Mb from the swap partition. If you had less than 550Mb of swap space, it may cause issues. When you never used swap, it sounds like there may have been issues with it turning on/ off.

In response to the second query, increasing the swap size could increase performance, but only if you were regularly using most of your RAM, swap. If you don't use much of the available RAM/ swap for everyday use, then I wouldn't recommend increasing the swap space.

---

### Post by Jackelope on 2008-08-21
Thanks for the help! I think I'll leave the swap alone then. At least until I reinstall when I screw something up playing around with stuff =\

---

