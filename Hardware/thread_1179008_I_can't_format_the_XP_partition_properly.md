---
title: "I can't format the XP partition properly"
date: 2009-06-05
forum: Hardware
---

### Post by mpolakovic on 2009-06-05
Hi guys.
 I have a little problem with my Xubuntu 9.04 installation on my DELL Latitude D505 notebook (an old one).
I had a dual boot of WinXP and Xubuntu for some time and now I decided to switch completely to Xubuntu. So I backed up all my content from the XP partition and formatted it to ext2 primary partition from GParted.
Since then, I'm unable to mount the volume.
When I wanted to mount it after the formatting, GParted gave me an error:
'Failed to mount "29G Volume". The enclosing drive for the volume is locked.'. I tried rebooting and then mounting the partition again with no success.
Then, I tried downloading a PartedMagic LiveCD (which returned correct md5hash), from which I first mounted the partition (!) and then formatted it to ext2 and mounted again.
I believe that the problem rests in my Xubuntu HW support, but I might be wrong.
I'm looking for any kind of advice that could possibly help me solve my problem.
Thanks in advance, Milos Polakovic.

---

### Post by mpolakovic on 2009-06-06
The problem solved itself somehow and my partition mounted.

---

