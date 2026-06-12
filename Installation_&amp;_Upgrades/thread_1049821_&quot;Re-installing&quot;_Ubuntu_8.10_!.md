---
title: "&quot;Re-installing&quot; Ubuntu 8.10 !"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by alexjean on 2009-01-24
Hello fellow Ubuntu lovers !):P

I recently discovered Ubuntu so I really need help from you guys here at Ubuntu forums.

I had an incident which led to the system not being able to log in. I type in user name+password, the pointer and my wallpaper appears for a second then the screen covers in a weird repetitive pattern all of a sudden and I'm brought back to the log in screen.

So I guess I should just "re-install" the operating system.
I boot the Live-CD from my USB-bootable drive and just click Install. When it comes to the partition stage I get confused.

**I want to use the same partition for the "re-install" as I installed it on before.**
So I should use 'manual', right? I go there and on the disk I want to use are 3 partitions:
/dev/sdb1 type: ntfs
/dev/sdb5 type: ext 3
/dev/sdb6 type: swap

I'm pretty sure 'ntfs' is the one that was left after installing last time and 'ext 3' and 'swap' were created when I set Ubuntu up last time. Doesn't that sound right?

If so, I delete 'ext 3' and 'swap' and make a new partition with the 'free space'. But what options do I chose there? and don't I have to make a new swap partition too ? :-k I would use 'guided' partition but it seems that if I use that sdb1, sdb5 and sdb6 are deleted and one big partition is made for the system... ?

Could someone tell me what to do at this stage (how to partition manually)?

---

### Post by taurus on 2009-01-25
Yes, use the Manual option and mount /dev/sdb5 to / and _format_ it.  You don't have to do anything with /dev/sdb6 since the installer knows how to handle swap partition.  If you want to mount /dev/sdb1 somewhere, you can do that too; otherwise, you can always mount your ntfs partition later if you wish.

---

### Post by tommcd on 2009-01-25
You could delete /dev/sdb5 and /dev/sdb6, and then create 3 partitions in the newly allocated free space:
a root partition for Ubuntu
a swap partition
a home partition for your files

You will need to choose manual partitioning for that. Root and swap could be primary or logical partitions. Make home a logical partition. The root partition can be 10-12GB if you have enough space. Make swap 2x RAM up to 1 GB, and the rest for home. Is /dev/sdb1 a Windows install, or just a NTFS data partition? If it is Windows you can set that to bootable. If it is just data then you could set Ubuntu's root partition as bootable.

---

### Post by alexjean on 2009-01-25
Thank you ! That was too easy hehe...\\:D/

Here is a [Cobra]("http://en.wikipedia.org/wiki/Cobra_(film)") 'poster' I "made" for all your hard work.. ! 

(The cobra is from a trailer and I recreated the 'STALLONE COBRA' logo...)

[IMG]http://img.photobucket.com/albums/v304/xanderz/cobraposterS.jpg[/IMG]

... I'm a fan ...

---

