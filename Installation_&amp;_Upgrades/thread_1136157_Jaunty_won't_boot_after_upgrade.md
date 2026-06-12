---
title: "Jaunty won't boot after upgrade"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by pjhudson on 2009-04-24
when it gets past the splash there is a box that pops up that says low graphics mode, but it freezes there and I can't do anything-- it effectively will not boot at all.

I'm pretty new to linux so any help would be appreciated--

on another note, when I upgraded from 8.04 to 8.10 I opted to not upgrade the grub loader because I was afraid of losing my windows boot-- so after it upgraded the menu never showed the new kernel, but I could boot in to 8.10 via the old kernel anyways- (strange?)-- well, the jaunty update is the same thing-- there is no kernel on the menu showing Jaunty, so I just chose the first kernel on the menu which was the original 8.04... (which had previously booted into 8.10), and were back to the top (of this post)...

I'm pretty tempted to just delete everything and start over again but I don't know how to do that.. as of now the only thing working on my laptop is windows

---

### Post by bngguy on 2009-04-24
> **pjhudson said:**
> when it gets past the splash there is a box that pops up that says low graphics mode, but it freezes there and I can't do anything-- it effectively will not boot at all.

I'm pretty new to linux so any help would be appreciated--

on another note, when I upgraded from 8.04 to 8.10 I opted to not upgrade the grub loader because I was afraid of losing my windows boot-- so after it upgraded the menu never showed the new kernel, but I could boot in to 8.10 via the old kernel anyways- (strange?)-- well, the jaunty update is the same thing-- there is no kernel on the menu showing Jaunty, so I just chose the first kernel on the menu which was the original 8.04... (which had previously booted into 8.10), and were back to the top (of this post)...

I'm pretty tempted to just delete everything and start over again but I don't know how to do that.. as of now the only thing working on my laptop is windows

If you dont have too many applications installed on 8.10, then i would recommend you to do a clean install, just download the Desktop Edition image(.iso), burn it on to a CD(700MB), pop it into ur CD/DVD drive and reboot, just click on the install icon on the desktop and follow the instructions.

---

### Post by pjhudson on 2009-04-24
I can do that without messing anything else up (with my windows partition?)--  I liked 8.04, it was working well and I only had a few issues with 8.10 which I hadn't used long enough to work out yet, so I guess I'll try that-- thanks

---

### Post by bngguy on 2009-04-24
> **pjhudson said:**
> I can do that without messing anything else up (with my windows partition?)--  I liked 8.04, it was working well and I only had a few issues with 8.10 which I hadn't used long enough to work out yet, so I guess I'll try that-- thanks

since u had already installed 8.04 and 8.10 , i'm assuming you have atleast a basic knowledge about disk partitioning, in 9.04 they have added an new filesystem (ext4), ext3 is very stable but ext4 has some bugs,read the release notes very carefully,you should probably stick with ext3

[http://www.ubuntu.com/getubuntu/releasenotes/904]("http://www.ubuntu.com/getubuntu/releasenotes/904")

---

