---
title: "I think Feisty fawn hates my CD writer"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by SunnyRabbiera on 2007-04-23
This is seriously wierd, my CD writer has just stopped working in feisty fawn for no apparent reason whatsoever.
It worked for my first few boots, but now, bam... gone, it doesnt work anymore now.
But the CD writer isnt bad, in fact it works fine if i pop in a older version of ubuntu and run it off the live.
I even took my compy to the geek squad to get her checked over, nothing wrong with the cd writer whatsoever...
I think there is something goofed in feisty fawn, this is definately not an issue with the company that makes my CD drive, it has worked before with a great deal of linux distro's so its not like its a linux hating CD drive, heck it seems to like linux.
Perhaps someone can help me out here...

---

### Post by bwhite82 on 2007-04-23
What exactly isn't working with it? Like not working at all (No lights, won't open, etc)? Or it can open, it can read CD's but can't write to them? Need more info.

---

### Post by SunnyRabbiera on 2007-04-23
well it opens and closes yes, but it wont read or write any disks.
even when i inserted a perfectly working CD it didnt mount my CD drive.
It seems to not want to mount my CD drive, no matter what I do.

---

### Post by SunnyRabbiera on 2007-04-24
this is a bump, as I seriously need this fixed.

---

### Post by Robin T Cox on 2007-04-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				See the bug URL above.

If this is the cause of your problem, there is now a work-round that cures this fault.

Add the word 'irqpoll' (without quotes) to the kernel line in /boot/grub/menu.lst thus:

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash irqpoll

Then Feisty will boot faster, and the CD burner will be recognised.

See:

[http://ubuntuforums.org/showthread.php?t=414002&page=2](http://ubuntuforums.org/showthread.php?t=414002&page=2)

---

