---
title: "First Ubuntu 12.04 doesn't work...now drivers aren't loading."
date: 2013-04-15
forum: Hardware
---

### Post by TheHomesk1llet on 2013-04-15
The other day, I tried booting into my 12.04 version of Ubuntu 32-bit, which I am running on a kernel capable of 64-bit but never really had the chance to replace it due to a lack of disk space. I found that the system would not boot from the current version of Ubuntu 12.04, so I booted from another version that I had, still 12.04. It was a pre-update system backup, so I believe the problem is related to updates. The thing was kernel panicking, saying that it was unable to mount root fs on unknown block, (0,0).

I tried installling Backtrack linux as well so that I would have an operating system that was ideal for the time being until I got Ubuntu working again. This caused the grub menu to be out of order and all of my Ubuntu versions listed in one menu, which was understandable. After shutting the computer down from Backtrack and rebooting it later, I was brought to a terminal prompt with the words "grub-rescue". I tried a few commands using the terminal, and attempted to boot the system from there, but the kernel would not load or the terminal would not recognize it. Since my computer was then without a boot manager, I had to boot from a live Ubuntu disk. I tried using the partition manager and the file browser to check the swap partitions and the system partitions, but everything looked normal. I even found the kernel where it was supposed to be, where I had told the grub menu to look for. I started to mess around with the terminal in the live disk, experimenting with commands that would install a new grub menu on the linux swap partition. It eventually worked (I don't remember exactly what commands I used, so don't ask) and I had a working grub menu. Ubuntu would now boot, as well, but the screen was at a very low resolution and slightly out of proportion. I also noticed that only my keyboard was working, I could not use my touchpad, and when I logged in, the wireless card wasn't working. Basically all drivers except the keyboard did not work, and this is how it is now. I can't connect to the internet on my computer with Ubuntu, and I don't know how I'm supposed to install the drivers, or have Ubuntu recognize them again.

So, forums...help?

---

### Post by TheHomesk1llet on 2013-04-19
Nobody knows? What a disappointing first experience with these forums. That combined with the fact that Ubuntu often crashes for me really tells a lot about the consumer's opinion of the consumer.

---

### Post by ahallubuntu on 2013-04-19
~

---

