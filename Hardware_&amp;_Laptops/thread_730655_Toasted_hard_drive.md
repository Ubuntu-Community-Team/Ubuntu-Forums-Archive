---
title: "Toasted hard drive?"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by kostyabkg on 2008-03-21
Good morning,

I have a weird problem with my laptop: Acer Aspire 5101 AWLMi, now running Ubuntu 7.10.

I always used only Windows that came together with laptop and nothing else. Then, one night it crashed (Blue Screen Of Death) and refused to start up, so I reinstalled the system from recovery DVD, it booted up, crashed and refused to start again, moreover in the POST screen it was no longer correctly identifying the hard drive: instead of writing IDE0: HTS541060G9AT00, it was saying something like: @;''""2_* and so on. So I thought, well, the Hard Drive has died and bought a new one.
Since the computer shut down in the middle of recovery with Acer Recovery Disc I put Ubuntu on it (crashed as well at first as soon as it was getting to loading menu selection, so I had to wait a little bit and everything was OK then). Here's where the interesting problems start to appear:
It all works fine until at some point of time the hard disc becomes read-only! No messages, nothing, just one of the applications stops working (being unable to write to the disc), I do `touch test` and, YES, the system became read-only again! So I reboot and it works fine again until some point in time. Looked in /etc/fstab and found the following options for /dev/hda1 "defaults,error=remount-ro", so I removed error=remount-ro, but it didn't help at all.

Possible hints(???): 
1. Sometimes when loading LiveCD Ubuntu complains about Critical Temperature being reached (95C) and shuts down.Usually I just wait, reboot and it all works fine.
2. At the startup the following messages is being displayed:
BIOS Bug found #81 (49435000).
I found the following links about that bug:
[https://bugs.launchpad.net/ubuntu/+bug/116734](https://bugs.launchpad.net/ubuntu/+bug/116734)
Which references these 2 pages
[http://www.fedoraforum.org/forum/showpost.php?p=901026&postcount=39](http://www.fedoraforum.org/forum/showpost.php?p=901026&postcount=39)
[http://ubuntuforums.org/archive/index.php/t-332829.html](http://ubuntuforums.org/archive/index.php/t-332829.html)

So it seems like BIOS bug #81 is irrelevant to  the problem.

Any help is greatly appreciated!

---

### Post by kostyabkg on 2008-03-22
The progress so far:
I ran memtest86+ and it discovered some memory errors, so I swap memory modules and everything seems to be working fine so far (the last 10 hours, fingers crossed).

---

### Post by nick_h on 2008-03-22
With problems like these testing the memory and hard drive is always a good idea.  I hope it has cured the problem for you.

---

