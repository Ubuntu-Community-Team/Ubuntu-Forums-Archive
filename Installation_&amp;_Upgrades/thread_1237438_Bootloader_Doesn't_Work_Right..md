---
title: "Bootloader Doesn't Work Right."
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by GRIMBEORN on 2009-08-11
Ooookay... So, I've been on computers all my life, but never strayed from Windows. I know my way around Windows like... Well, I would say the back of my hand, but who HONESTLY knows the back of their hand?

My problem is this. I'm trying to dual-boot Windows XP SP3 32-bit and Ubuntu Netbook Remix. The problem I'm having is that GRUB(?) doesn't want to load my XP install. I'm not exactly sure what I did wrong. After several tries to fix this problem, not knowing precisely what I'm doing, everything just... Exploded. Both installs became useless. So, now I've just got XP SP3, again, after some formatting, and I think I need some person to person help doing this, lest I screw is up again.

What I mean to say is, "Help, please! I have no idea what I'm doing, even after reading the manuals. Most jargon confuses me until I've heard it >9000 times."

If it helps, Ubuntu ran fine while I wasn't trying to get XP back. I just don't know what I did wrong with GRUB. Actually, I don't even remember what I did. I've been up all night fretting about my computer, so I may not be the smartest chap, right now... Also, I run a stock HP Pavillion dv6629wm Entertainment Notebook, if that helps.

I want to have a main partition of XP with a small Ubuntu partition. I'm interested in learning to use Ubuntu, but I don't like to get used to new OSs without a safe, working OS already there for me to run back to when I get scared...

---

### Post by phillw on 2009-08-11
That's no problem ..

there is a super little thing called SuperGrub, that covers most options, painlessly...

Here is a link to a tutorial for it.

[http://en.kioskea.net/faq/sujet-2677-super-grub-disk-live-cd](http://en.kioskea.net/faq/sujet-2677-super-grub-disk-live-cd)

Regards,

Phill.

---

### Post by raymondh on 2009-08-11
> **GRIMBEORN said:**
> Ooookay... So, I've been on computers all my life, but never strayed from Windows. I know my way around Windows like... Well, I would say the back of my hand, but who HONESTLY knows the back of their hand?

My problem is this. I'm trying to dual-boot Windows XP SP3 32-bit and Ubuntu Netbook Remix. The problem I'm having is that GRUB(?) doesn't want to load my XP install. I'm not exactly sure what I did wrong. After several tries to fix this problem, not knowing precisely what I'm doing, everything just... Exploded. Both installs became useless. So, now I've just got XP SP3, again, after some formatting, and I think I need some person to person help doing this, lest I screw is up again.

What I mean to say is, "Help, please! I have no idea what I'm doing, even after reading the manuals. Most jargon confuses me until I've heard it >9000 times."

If it helps, Ubuntu ran fine while I wasn't trying to get XP back. I just don't know what I did wrong with GRUB. Actually, I don't even remember what I did. I've been up all night fretting about my computer, so I may not be the smartest chap, right now... Also, I run a stock HP Pavillion dv6629wm Entertainment Notebook, if that helps.

I want to have a main partition of XP with a small Ubuntu partition. I'm interested in learning to use Ubuntu, but I don't like to get used to new OSs without a safe, working OS already there for me to run back to when I get scared...

Just to confirm ...

You are now solely booting windows XP, right? 
You have no problems booting into XP?

You want to dual-boot ubuntu .... and need help installing as the previous ubuntu install had GRUB problems?

If so :

1.  back up your files
2.  Defrag windows again
3.  Check the liveCD for defects and [MD5]("https://help.ubuntu.com/community/HowToMD5SUM")

Some reference links:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Some links should you run into the GRUB problem again:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

If my questions/assumptions were wrong, I apologize ... I did not/could not understand your issue.  

While on liveCD and in "live session", could you access a terminal (applications > accessories) and type and post back the output of:

```
sudo fdisk -l
```

this can give the forum an idea of your current HD partitions ... with or without Ubuntu.

---

