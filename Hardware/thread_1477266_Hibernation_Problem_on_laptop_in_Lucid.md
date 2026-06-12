---
title: "Hibernation Problem on laptop in Lucid"
date: 2010-05-08
forum: Hardware
---

### Post by sharathcshekhar on 2010-05-08
Hi All,
I installed Lucid (64 bit) a few days back on my HP DV6000 AMD-64 laptop. Everything seems to work fine except for the hibernation. 
I searched a lot of threads and some of the people are unable to restore from hibernation. However, the problem I am facing is a bit different.. When I hibernate, everything goes fine but the laptop is not powered off. Fan and hard disk will still be running and I'll have to manually power off by holding the power button. But when I power on the laptop again, I am facing no problems and the hibernated image is reloaded. 
I used to use hibernation a lot before and it was working fine till Karmic. I used to face the same problem in Jaunty, but it started working fine after I recompiled the dsdt file as indicated in the following howto.
[http://ubuntuforums.org/showthread.php?t=1036051]("http://ubuntuforums.org/showthread.php?t=1036051")

But that post says, that method does not work from Karmic and above. But surprisingly, when I upgraded to Karmic I did not face issues. But now I did a clean install for Lucid and the problem is back. 
I gave a try to do the same procedure for the dsdt file I had done for Jaunty, but it did not work. Is recompiling the kernel with custom dsdt patch only option?
I have attached the output of /var/log/messages and dmesg output. Though I have been using Ubuntu for a while, I am unable to figure out what is going wrong. 

If anybody can interpret these logs to find out the problem, please help me in getting back my laptop to hibernate :(
Any help is appreciated. Thanks in Advance.

PS: Suspend is working fine.

--
Sharath

---

### Post by peleg on 2010-05-09
I have just discovered, that I have exactly the same issue!

My problem is also, not about recovering from hibernation, but about going into hibernation. I am on a very fresh install of lucid - and while hibernation worked great once or twice since the new installation, it does not work at all in the last few days.

The screen becomes dark, but the computer is still working. When I press something, it comes back and asks for a password. But it uses electricity.

I suspect that one of the latest updates that I have installed since the fresh installation causes this (can't be sure, though).


I'll appreciate any help.
Thanks!


PS: suspend works here as well.

---

### Post by eroeurbano on 2010-06-07
Same issue for me.
I had trouble on my HP DV6000 with previous releases that I solved by recompiling the dsdt file.
I made a fresh installation of Ubuntu 10.04. Now suspension works fine,
but Hibernation doesn't turn off the computer.
However if I turn off manuallly everything goes fine at restart.
If it can help when I Hibernate appears a mesage like:
>  [some code] btusb_bulk_complete hcbi0 urb xxxxxxxx failed to resubmit 
Any help would be appreciated.
Cheers, -Luca

---

### Post by veggen on 2010-07-04
Same here on suspension on my desktop. While recovering. I get the dreaded "failed to resubmit" message. Does anyone know if this bug is reported? Any advice what we might try to do to sort this out? 

It's fairly serious issue... and for f***'s sake, it's [over a year](http://ubuntuforums.org/showthread.php?t=1178210) [old](http://ubuntuforums.org/showthread.php?t=1158909), yet it never, ever got **any** attention.

---

### Post by kodanda on 2010-08-17
Same issue here as well! did anybody find a solution?

thanx
kodanda

---

### Post by anoknusa on 2010-09-01
Bad news: seems you need to build your own kernel, using the custom dsdt file in the process.  I've been dealing with the crap Toshiba owners get dealt to them when using linux, and all the research I've done has led me to that conclusion.  I've never built a custom kernel, so this should be an interesting learning experience.  I'm kinda desperate, and have comprehensive backups, so I have no problem messing around with this. 

If you want, you can check out these links:

[How-to: use custom DSDT in Karmic]("http://ubuntuforums.org/showthread.php?t=1341580")

[URL="http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/"]
How to compile a Ubuntu Lucid kernel[/URL]

Best of luck.

---

### Post by sharathcshekhar on 2010-09-05
Thanks for your replies. I actually Installed the i386 version of Lucid on my laptop instead of 64 bit version. And Hibernation seems to work perfectly all right without even recompiling the dsdt file!
Guess there is some problem with the 64 bit Kernel in dealing with old BIOS like mine.

---

