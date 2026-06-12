---
title: "Setting Up a Dual Boot System"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by MarkBeauchene on 2006-02-04
So much seems really great about this OS, so I'd like to set up a dual boot system to try it out.  I'm using a Toshiba notebook, and need to reload the whole thing anyway to clean out all the junk I've accumulated.  It runs so slow you could say it crawls, but with a 1.6 G P4 it shouldn't be that bad.

So I can't find a simple set of instructions on how to set everything up.  Can someone out there send me or post what I need to do?

---

### Post by taurus on 2006-02-04
If you bother to look around or use the Search, you will find there are a tons of posts regarding dualboot.  In other words, create two partitions.  Install XP on the first partiton and when XP is done, boot Ubuntu and tell it to use the second partition.  However, you need to use the second partition to create at least two partitons:  one for / and one for swap.  When you get to the step about bootloader, use GRUB and have it install on MBR.  GRUB should be able to pick up your XP and adds an entry in /boot/grub/menu.lst for you so that when you boot, you have an option to boot either Ubuntu or XP.

---

### Post by Herman on 2006-02-04
> So I can't find a simple set of instructions on how to set everything up. Can someone out there send me or post what I need to do? Sure, taurus's explanation is a pretty good summary of it.
If you want to find out more, click on my first signature link, a lot of people look at those examples before installing. It's not compulsory to do yours the same, but you can see how the installer and partitioner work in advance. You can do something like one of those examples if you wish, there are three to choose from. Or make up your own partitioning scheme. Some people like it more elaborate. I pefer simplicity (The first (fat32) is my favourite). Enjoy! :-D (Herman)
PS, since it's a notebook, use a little extra caution and try the 'live CD' out to make sure your hardware will work, and/or check the supported laptops list if you want. I have an Acer notebook with a wide screen and I installed Ubuntu in it, but I was worried for a while since the bottom of the display was not showing, I had to use my own website to help me choose the right selections a few times, counting the key presses, and working 'blind'. In the end the monitor resolution chooser came up and everything was fine after that. maybe I should have tried the 'expert' install instead. Anyway, it's good now.

---

### Post by MarkBeauchene on 2006-02-04
[QUOTE=taurus]If you bother to look around or use the Search, you will find there are a tons of posts regarding dualboot.


I tried many searches, but failed to make dual boot into one word.  I'll try it now.

By the way, i appreciated your response.  Thanks.

---

### Post by strebor71 on 2006-02-04
i am in the same spot as you Mark. I happened to find hermans web site and i found that it was exactly what i needed to ensure me that i could pull this off with out any worries. great job Herman. its nice to now that some people that reply to requests for help actually try and help. Some of us dont know everything, and appreciate it when someone truly makes an atempt to help us as we learn. heres a link to the page im refering to. 

[http://users.bigpond.net.au/hermanzone/index.htm]("http://users.bigpond.net.au/hermanzone/index.htm")

---

### Post by Herman on 2006-02-04
Thanks, Strebor71, I thought no-one noticed. Maybe i was too wordy and the suggestion for the link got lost in the text. Thanks. :-D (Herman)

---

