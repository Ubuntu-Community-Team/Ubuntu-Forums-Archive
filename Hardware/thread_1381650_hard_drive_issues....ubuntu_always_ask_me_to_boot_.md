---
title: "hard drive issues....ubuntu always ask me to boot in fsck manually"
date: 2010-01-15
forum: Hardware
---

### Post by hockey97 on 2010-01-15
Hi, I have 2 hard drives in one computer. I have dual boot one hard drive is ubuntu and the other is windows xp professional mixed with ubutnu as extra storage for ubuntu os.

Currently when I boot into ubuntu. I would always get told to run fsck manually to fix hard drive problems. I do what it asks and hit yes to fix each item when it pop's up and asked if they should delete or fix this sector etc.

at the end it asks to reboot my pc. Which I do... and then it boots normally.

I have to do this every time I shut down the computer and have to boot again in ubuntu. Is their any software that I can use at boot to examine hard drives to see if their is any faults or anyhing?

When I use windows xp sometimes not all the time but it at times will show a error message at boot saying missing certain files please use the windows xp cd to repair missing files. When I get this message I just turn off the pc and turn it back on for about 5 times but it's usally random... and then it works perfectly as if it had not trouble booting.

Do you think my hard drives are starting to fail? I would like to know if their is any software that would fix any problems my hard drive may have.

---

### Post by jdeca57 on 2010-01-24
Two remarks: I had a problem on the root partition of my hard drive in ubuntu. Apparently fsck didn't work on the active drive and I solved it using the live CD. On the other hand, it might be caused by a failure on the xp drive, and the ubuntu data partition gives the error. That would be hardware, since xp also gives problems. And (ok, that's a third remark) if both drives fail simultanious, I'd look at other hardware (power supply, motherboard). Hope this helps..

---

