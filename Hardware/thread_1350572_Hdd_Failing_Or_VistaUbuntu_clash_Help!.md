---
title: "Hdd Failing? Or Vista/Ubuntu clash? Help!"
date: 2009-12-09
forum: Hardware
---

### Post by darkdemon923 on 2009-12-09
I installed ubuntu using Wubi on my laptop. It has windows vista home premium. After i installed ubuntu and started using it gave me a pop saying that my hard drive is probably failing. I dont know why this is. Can some one help me? Is it possibly just because i installed ubuntu on the same drive as vista and it cant access vista files? It said something about my boot sectors. Please help i am looking forward to using ubuntu. And i can still run vista as well.

I have 160 gig hard drive with over 30 gigs of space left.

---

### Post by VernonA on 2009-12-09
Karmic ships with a tool called Palimpsest installed, which is a utility to monitor the health of your hard drive(s). It runs automatically when you start Ubuntu and pops up the warning dialog you mention if it detects problems. (Modern hard disks use S.M.A.R.T. technology to test themselves and then try to predict when they might fail before they actually do.)
The good news is that this is not a bug in any way. It is correct behaviour - you don't see anything when you boot Windows because that O/S is not as good as Ubuntu;-)
The bad news is that you might indeed have a hard drive that will soon fail. Make sure you get into the habit of backing up your important info to another medium. If you have a new drive, you might have run into a bug in Palimpsest. See, for example, [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136)

---

