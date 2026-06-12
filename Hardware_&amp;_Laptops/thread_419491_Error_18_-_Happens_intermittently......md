---
title: "Error 18 - Happens intermittently....."
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by wbishop311 on 2007-04-23
Hi all,

I've been a Ubuntu user for for a little bit now, and I must say, from what I have read in the forums, the Ubuntu community seems to be a lot friendlier than those with the other distributions I have run.  This is reassuring,  lol :-D  I still sorta consider myself a newbie, though I'm moving along quite nicely (also thanks to Ubuntu's user friendliness).

Maybe every 20 or so times I boot my machine, I get an error:

Error 18 - Selected cylinder exceeds maximum supported by BIOS

The only posts or info I can find are from users who get this message all the time, not occasionally like myself, so I am wondering if this is a potential hard disk failure or if it's just something I need to tweak.  

I'm almost certain you will need more info, as this seems like a really vague error and description, but here's my fdisk -l -- if it helps:

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7207    57890196   83  Linux
/dev/hda2            7208        7297      722925    5  Extended
/dev/hda5            7208        7297      722893+  82  Linux swap / Solaris


I'm just running a 1.2 Ghz AMD Duron, 60 gig IDE HD, nothing fancy.  Anyone have any suggestions?  I'm not really sure how to check the limitations of my motherboard (aside from looking for the manual), but I haven't really had this problem with other distros or Windows.

Thanks so much for your help.  I'm a new member, so this will be the first of many dumb questions I will ask.  I apologize in advance, haha :-D

Thanks,

Bill

---

### Post by tommcd on 2007-04-23
See this thread:
[http://ubuntuforums.org/showthread.php?t=417447](http://ubuntuforums.org/showthread.php?t=417447)
This user fixed the problem by reinstalling ubuntu and setting it up with a 8GB /root partition, a 1GB swap, and the rest /home. The problem in his case was an old motherboard and the bios could not read a partion beyond a certain size. 
Another option is to reinstall and create a small (100mb) /boot partition at the begining of the disk and install grub to that.
Search around though, there may be other ways to solve this.

---

### Post by wbishop311 on 2007-04-23
Thanks a million, I appriciate the response :-D  I will check the link out too and see what I can do.  I'll let ya know :)

Thanks again :)

Bill

---

