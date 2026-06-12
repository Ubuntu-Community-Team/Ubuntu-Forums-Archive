---
title: "Thinkpad T400 wireless problem, fix, and questions"
date: 2008-11-08
forum: Hardware
---

### Post by fstonedahl on 2008-11-08
I have Thinkpad T400, with Ubuntu 8.10, with this wireless card (from lspci)

"Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)"

I'd gotten it working using the madwifi drivers (I first tried the ath5K open source ones, but for some reason they were really really slow/unresponsive).

Then yesterday Ubuntu notified me of some updates, including some kernel update 2.6.27-7, so I installed them.  After that, my wireless didn't work at all (ifconfig didn't even list any "ath0" interface.)  After a bit of digging, I found this post:

[http://ubuntuforums.org/showthread.php?t=940048&highlight=t400](http://ubuntuforums.org/showthread.php?t=940048&highlight=t400)

And I tried "sudo apt-get install linux-backports-modules-intrepid", which seems to have fixed the problem.

HOWEVER, while it's one thing to have it working, it would be even better to understand it.  So I would love it if someone more knowledgeable than me about Linux and Ubuntu could answer a couple questions for me:

1) Why might my wireless have stopped working when I did the updates Ubuntu suggested to me?  Should I be careful not to update the kernel in the future, for fear of breaking existing hardware configurations?  I know madwifi is a module, which is loaded by the kernel.  But I guess I don't know what happens to modules when the kernel gets upgraded... should they still work?

2) What is in this "backports" package, and why might it have fixed my problem?

Thanks for any shared wisdom! ~fstonedahl

---

### Post by cariboo on 2008-11-08
There is a bug in the ath5K driver that makes it not play nice with madwifi. Using the backports package intstalls an updated driver that is not in the kernel yet.

The backports repository is where all the new packages go that haven't been integrated in to the distribution yet.

Jim

---

### Post by fstonedahl on 2008-11-08
Great, thanks for your reply.

---

