---
title: "Making a Swap partition post installation"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by geekity2 on 2009-04-06
Hi, I'm a newbie to this forum. I've been dabbling in ubuntu user-style (basically I know enough to get me in trouble) for a while now and figure it's about time to get more into the system and such.

Anywho, I'm currently running intrepid dual boot with XP, at least until jaunty comes out, that someone installed for me when it first came out. Unfortunately they didn't make a swap partition (dunno why, really) at the time of install. So, I was wondering whether there's a way to make a swap partition now without having to reinstall the OS?

Apologies if this question has been addressed before.

Nina

---

### Post by TrickerZ on 2009-04-06
Yes, there is.  You need to use disk partitioning software that supports resizing partitions, create a partition, label it as swap, boot into your linux OS, type "mkswap /dev/<partition>" and then put the partition in your /etc/fstab file something like "/dev/sda5 swap swap sw,pri=1 0 0" save and type swapon -a and it should be activated.  You can do "cat /proc/swaps" to see if your partition is up and running.  Try a reboot and see if it's comes up on boot.

---

