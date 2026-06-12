---
title: "Ubuntu doesn't show up after install!"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by Incitecite on 2009-07-17
I just installed Ubuntu 9.04 on my desktop. I have used the GAG (graphical boot manager) for some time, so I opted not to install GRUB when I installed Ubuntu. However, GAG only shows Windows, no ubuntu. Could this be because GAG doesn't support the ext3 filesystem? Things seemed to go smoothly during the installation process, so I find this very strange, and GAG has never given me trouble before (in fact, it's rescued me several times in the past!). 

I tried to install grub again without any success from the live CD as well. After I type 
find /boot/grub/stage1 it returns something like "error 15: location not found."

I'm at a loss. Any suggestions?

---

### Post by presence1960 on 2009-07-17
It looks like you have to manually add Ubuntu. here is the info from GAG's web page. I personally would stick with GRUB: [GAG web site]("http://gag.sourceforge.net/pics.htm")

Of course find /boot/grub/stage1 is not going to find anything because you didn't install GRUB!

---

### Post by Incitecite on 2009-07-17
The problem with GAG is that it's not even showing the ubuntu partition that I just created. Even if I had to manually set it up, that would be a non-issue. It appears that I need to to install grub. Most of the threads related to this seem to be about restoring grub after installing another OS, not about setting it up initially (which is what I need  to do). Is there a simple command to do this from the ubuntu live CD? I would fiddle around with it more, but I'm being overly cautious to make sure I don't do something wrong and end up with an unbootable computer.

It looks like using the terminal on the liveCD and typing grub-install is the easiest method, but I really have no idea what I'm doing.

---

### Post by merlinus on 2009-07-17
Here is some info:

[http://www.gnu.org/software/grub/manual/html_node/Invoking-grub-install.html#Invoking%20grub-install](http://www.gnu.org/software/grub/manual/html_node/Invoking-grub-install.html#Invoking%20grub-install)

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub-install.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub-install.html)

---

### Post by Incitecite on 2009-07-17
I've fixed it! Apparently the issue was a lot more simple than I had thought. I used super grub disk to boot into ubuntu, installed grub from there, but nothing happened, so I deleted the ubuntu partition, reinstalled ubuntu, but nothing happened. Then it occurred to me that I have 2 HDDs, winXp booting off the first and ubuntu off the second, so I switched the boot order to use the ubuntu drive first, and it ran Grub instead of GAG, both OS's were shown, and everything seems to be working fine. I feel like an idiot for not realizing this before, but at least everything is as it should be now.

Thanks for your help guys. :)

---

